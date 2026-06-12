---
title: "How to have a folder for access RW for parents and R for childrens?"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by honeybear on 2011-06-13
Hello

/home/partagerepertoire must be such as have a folder for access RW for parents and R for childrens. How could I do such things actually on the linux machine? 

chmod or adduser would be adviced, right? 

Cheers

---

### Post by Derek Karpinski on 2011-06-13
assuming 'partagerepertoire' is the owner and the group is set to partagerepertoire, and 'partagerepertoire' is the user you're logged in as:
 
```
chmod -R /home/partagerepertoire 774
```
 
that gives full read/write/execute permissions to the user who owns the directory, full rwx to the group, and read only to others.  The -R applies those permissions to every file and subdirectory inside /home/partagerepertoire
 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by honeybear on 2011-06-13
> **Derek Karpinski said:**
> assuming 'partagerepertoire' is the owner and the group is set to partagerepertoire, and 'partagerepertoire' is the user you're logged in as:
 
```
chmod -R /home/partagerepertoire 774
```
 
that gives full read/write/execute permissions to the user who owns the directory, full rwx to the group, and read only to others.  The -R applies those permissions to every file and subdirectory inside /home/partagerepertoire
 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

maybe I should create group:
  parents
  children

but then how to chgrp the folders into /home/partagerepertoire... ?

---

### Post by Omar.Fayyad on 2011-06-13
> **honeybear said:**
> Hello

/home/partagerepertoire must be such as have a folder for access RW for parents and R for childrens. How could I do such things actually on the linux machine? 

chmod or adduser would be adviced, right? 

Cheers


Hello there,

Just for simplisty, i would assume your parents username are as follow a,b and c,d for the childern.

First, you have to associate a and b to group called parents and c and d to a group called childern and this is as follow:

groupadd  parents
groupadd childern

usermod -G parents a
usermod -G parents b

usermod -G childern a
usermod -G childern b

After that you create the folder and associate the group owner of the folder to be for the "parents" group we just created and the owner is your username, and it is done as follow:

mkdir <path to the folder>    for e.g. mkdir /home/micheal/testfolder
chgrp parents /home/micheal/testfolder
chmod 775 /home/micheal/testfolder


I would also advise that you follow the below link and have a quick look.
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Please let me know, how it worked and also am available for further help

---

### Post by honeybear on 2011-06-13
Thank you. That helped.

A question.

I have a folder: 
```
Medicine rwxrwxr-x root parents
```
Medicine/file1 rwxrwxr-x root parents
Medicine/folder1 rwxrwxr-x root parents
Medicine/file2 rwxrwxr-x parents parents
Medicine/folder2 rwxrwxr-x parents parents


Can the childrens rename or delete Medicine folder?
Can the childrens rename or delete Medicine folder1 into Medicine?
Can the childrens rename or delete Medicine file1 into Medicine?
Can the parents rename or delete Medicine folder?
Can the parents rename or delete Medicine folder1 into Medicine?
Can the parents rename or delete Medicine file1 into Medicine?

I still dont get what for is chmod +t Medicine... 
This sticky is not needed since the root is owner of Medicine ...

---

