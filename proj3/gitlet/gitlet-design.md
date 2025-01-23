# Gitlet Design Document
author: Morgan Lyu

## Design Document Guidelines

Please use the following format for your Gitlet design document. Your design
document should be written in markdown, a language that allows you to nicely 
format and style a text file. Organize your design document in a way that 
will make it easy for you or a course-staff member to read.  

## 1. Classes and Data Structures

Include here any class definitions. For each class list the instance
variables and static variables (if any). Include a ***brief description***
of each variable and its purpose in the class. Your explanations in
this section should be as concise as possible. Leave the full
explanation to the following sections. You may cut this section short
if you find your document is too wordy.

**Blob** - instance vars include
* file content
* file name

**Commit** - instance vars include
* commit message - log that describes the commit
* timestamp - when the commit is made
* mapping between file names and blobs
* parent refs (2 for merge) - what the parent commit is/are

**Commands** - where various directories (vars) and commands(methods) are defined.

## 2. Algorithms

This is where you tell us how your code works. For each class, include
a high-level description of the methods in that class. That is, do not
include a line-by-line breakdown of your code, but something you would
write in a javadoc comment above a method, ***including any edge cases
you are accounting for***. We have read the project spec too, so make
sure you do not repeat or rephrase what is stated there.  This should
be a description of how your code accomplishes what is stated in the
spec.

The length of this section depends on the complexity of the task and
the complexity of your design. However, simple explanations are
preferred. Here are some formatting tips:

* For complex tasks, like determining merge conflicts, we recommend
  that you split the task into parts. Describe your algorithm for each
  part in a separate section. Start with the simplest component and
  build up your design, one piece at a time. For example, your
  algorithms section for Merge Conflicts could have sections for:

   * Checking if a merge is necessary.
   * Determining which files (if any) have a conflict.
   * Representing the conflict in the file.
  


* **init** - create inital commit with specified msg, store it in commit directory,
update contents of HEAD.txt to current branch "master", store the current branch in branch directory
* **add** - make a new blob, 
* **commit** - create a commit file with parent as previous commit + other info, put into commit
directory. move branch pointer to the newly created commit.
* **rm** - 
* **log** - for every commit in the commit tree, print the required info. 
Access the info by instance vars, the tree by parents.
* **checkout file name** - retrieve the version of the file/blob in head commit through filename + TreeMap 
and overwrite the file by the same name in CWD
* **checkout commit id file name** - pretty much same as above, use commit id to get the specified commit
first instead of using head commit.
* 

## 3. Persistence

Describe your strategy for ensuring that you don’t lose the state of your program
across multiple runs. 

Will use serialization and write appropriate files in corresponding directories
to save them so they can be read later. Commits, blobs, branch structures are 
needed across multiple calls to restore previous versions. Specifically commit trees are immutable
so it would always persist.

  
* This section should also include a description of your .gitlet
  directory and any files or subdirectories you intend on including
  there.
  * working directory - where working files and gitlet dir is located
    * gitlet directory - contains the following
      * add directory - stores files staged for add
      * rm directory - stores files staged for rm
      * branch directory - stores commit id
      * commit directory - stores commit info
      * blob directory - stores file content
      * HEAD.txt - stores the name of current branch

* This section should be structured as a list of all the times you
  will need to record the state of the program or files. For each
  case, you must prove that your design ensures correct behavior. For
  example, explain how you intend to make sure that after we call
  `java gitlet.Main add wug.txt`,
  on the next execution of
  `java gitlet.Main commit -m “modify wug.txt”`,
  the correct commit will be made.
  * after we call add wug.txt, we add the txt to the add directory in the staging area. 
  Then when we call commit, it'll take a snapshot of the file and save it across multiple runs.

## 4. Design Diagram

Attach a picture of your design diagram illustrating the structure of your
classes and data structures. The design diagram should make it easy to 
visualize the structure and workflow of your program.

![](../../../Desktop/Screen Shot 2022-04-25 at 12.33.39 PM.png)