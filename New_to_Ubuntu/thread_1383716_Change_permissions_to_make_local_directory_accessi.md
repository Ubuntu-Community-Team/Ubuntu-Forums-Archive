---
title: "Change permissions to make local directory accessible to other users"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by stevieP on 2010-01-17
I have a simple problem which I hope has a simple solution. I want to make a local directory of mine (call it "Dir3", with full path /home/steviep/Dir1/Dir2/Dir3/) visible to other users, so they can access the files and subfolders contained therein. 
I have tried the following:

$ cd  /home/steviep/Dir1/Dir2/
$ ls
Dir3   file1   file2
$ chmod a+rwx Dir3
$ ls -l
drwxrwxrwx 31 steviep steviep   4096 2009-10-06 16:05 Dir3
-rwxr--r--  1 steviep steviep 156993 2009-04-21 21:08 file1
-rwxr--r--  1 steviep steviep 156993 2009-04-21 21:08 file2


I should note that the permissions of Dir1 and Dir2 are  
drwxrwxr-x 26 steviep steviep    4096 2009-11-25 21:29 Dir1/
and
drwxr-xr-x  4 steviep steviep    4096 2009-05-11 18:23 Dir2

Now since I have root permissions I have made another account and tried to access this folder:

otheruser@comp:~$ cd ../steviep/Dir1/Dir2/Dir3/
-bash: cd: ../steve/Dir1/Dir2/Dir3: Permission denied

So my question is: is it possible to make a local directory in my account (with all its files and subfolders) accessible to other users on the same computer, without having my higher level directories (Dir1/ and Dir2/ here) accessible? If so, how? 

Thanks, 

steviep

---

### Post by tom4everitt on 2010-01-17
In order for a user to cd into a directory is that the user has executition permission for the directory.

So for this other user to be able to cd into your directory (or create a symbolic link to it for that matter) he needs to have execution permission to every folder in the path to it. 

Execution permission does not, as you may know, enable that user to list the files in your directory or make any changes to it, and he can only cd to sub-directories of which he has execution permission, so its pretty safe.

---

### Post by tom4everitt on 2010-01-17
Oh, one more problem that may arise is that if you create files in this directory, they will take the standard permission (not full permission). 

The only way to fix this I guess is to keep the folder on another partion and mount that partition with umask=000 or something (so the standard permission becomes full permission). I don't know of any way to set umask for just a folder.

---

### Post by sisco311 on 2010-01-17
> **tom4everitt said:**
> I don't know of any way to set umask for just a folder.

You can't. You have to use ACLs: [uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

---

### Post by stevieP on 2010-01-17
OK Thanks, I see. I did not have group/other permissions to access execute commands in my home directory. 
so, 
$ chmod go+x /home/steviep

made the directory readable. 

HOWEVER, I am not happy with this arrangement. While the other user can see this directory and list the contents, which is what I sought, he/she can also list contents in higher level directories (if the files have group and other read permissions) as follows.

These are commands the other user can execute:
 
```
$ cd /home/steviep/Dir1/Dir2/Dir3/
user@comp:/home/steviep/Dir1/Dir2/Dir3$ ls
(lists numerous files)
user@comp:/home/steviep/Dir1/Dir2/Dir3$ cd ..
user@comp:/home/steviep/Dir1/Dir2$ ls
ls: cannot open directory .: Permission denied
```

(so apparently the user cannot list the files here because that folder does not have read permissions, its permissions are: drwx--x--x )

However if the user *guesses* the names of files or folders, they can list them if they are themselves world-readable, e.g. 

```
user@comp:/home/steviep/Dir1/Dir2$ ls 
ls: cannot open directory .: Permission denied
user@comp:/home/steviep/Dir1/Dir2$ ls Programs
ls: cannot access Programs/Analysis: Permission denied
ls: cannot access Programs/Energy: Permission denied
ls: cannot access Programs/tmp: Permission denied
ls: cannot access Programs/Calc: Permission denied
ls: cannot access Programs/Confidential: Permission denied
ls: cannot access Programs/Friends: Permission denied
ls: cannot access Programs/Lovers: Permission denied
Analysis   Calc   Confidential   Energy    Friends   Lovers  tmp

```
they cannot list the contents of the subfolders because "Programs" is not world executable, but they can see what files/folders were there.

Given this situation and the fact that the user can guess as much as they want about what files/folders they might want to look for, I think I would prefer to actually just copy the folder to an external disk or another computer. 

Thanks, 

steviep

---

### Post by tom4everitt on 2010-01-18
Yes, you're right about the other user being able to "guess" until he finds out whats in your super folders. I didn't think this was possible (seems sort of stupid to me, but there's probably a reason for it). 

If you don't want to just keep a copy on some external drive you can create a separate partition (on your own hard drive or elsewhere), and mount it to the place of your folder and simultaneously mount it to somewhere in your other users folder tree with mount --bind.

---

