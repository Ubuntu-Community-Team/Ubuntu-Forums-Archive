---
title: "remove delete permissions"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by babyrajT on 2008-06-17
Hi All,

I have created folder in root named /samba and I have share this folder .I can access thgis folder from windows and also have the rwx permissions .The thing is I want to remove the delete permission to this folder without removing the write permission.Is there any way to do that?


Thnaks

---

### Post by nycste on 2008-07-14
not sure if im asking the same thing as the guy who started this thread

but ive read many threads trying to figureout similiar things and well sadly no response to this thread in 3 weeks being open

soo ill post my question/concern issues

1. im a linux newb
2. im a ubuntu newb
3. i love learning this crap

issues

i wanted to make backups of firefox and thunderbird so i compressed the two folders in home dir but had to show hidden files

i didnt realize that the compressed files i made were also hidden, so i figured thats fine

i then transported them to my windows partition to where i keep my backup files and well i didnt see the files when i moved them so i was confused

finally figured out that they were hidden, soo i havent gone into windows or anything yet but i have a feeling these files might be unuseable in windwos? yes/no i dont know

bottom line is... how do you remove root/hidden permissions on these select files, or any specific file/folder for that matter

i saw someone mention in another thread do this

ls -l folder_name

so i did and it said

ls -l .mozilla.tar.gz
-rw-r--r-- 1 username username 76288511 2008-07-14 20:38 .mozilla.tar.gz

---

### Post by smo0th on 2008-07-15
> **babyrajT said:**
> Hi All,

I have created folder in root named /samba and I have share this folder .I can access thgis folder from windows and also have the rwx permissions .The thing is I want to remove the delete permission to this folder without removing the write permission.Is there any way to do that?


Thnaks

Hello babyrajT,

you can do this by using the sticky bit, modify your samba directory by typing the following:

```
chmod +t samba -R
```

with this, only the file owner, root or a super user has priviledges to delete files from your samba folder. The -R option stands for recursive and applies changes to sub-folders.

---

### Post by smo0th on 2008-07-15
> **nycste said:**
> not sure if im asking the same thing as the guy who started this thread

but ive read many threads trying to figureout similiar things and well sadly no response to this thread in 3 weeks being open

soo ill post my question/concern issues

1. im a linux newb
2. im a ubuntu newb
3. i love learning this crap

issues

i wanted to make backups of firefox and thunderbird so i compressed the two folders in home dir but had to show hidden files

i didnt realize that the compressed files i made were also hidden, so i figured thats fine

i then transported them to my windows partition to where i keep my backup files and well i didnt see the files when i moved them so i was confused

finally figured out that they were hidden, soo i havent gone into windows or anything yet but i have a feeling these files might be unuseable in windwos? yes/no i dont know

bottom line is... how do you remove root/hidden permissions on these select files, or any specific file/folder for that matter

i saw someone mention in another thread do this

ls -l folder_name

so i did and it said

ls -l .mozilla.tar.gz
-rw-r--r-- 1 username username 76288511 2008-07-14 20:38 .mozilla.tar.gz

when browsing a directory with nautilus(system graphical file browser) you can see hidden files by pressing ctrl+h, 

> how do you remove root/hidden permissions on these select files, or any specific file/folder for that matter

you don't want to remove root permissions and you unhide a file by removing the '.' at the beginning of the file, like:
```
sudo mv .mozilla.tar.gz mozilla.tar.gz
```

if you want to set write permissions for you, change the file ownership with ```
sudo chown nycste .mozilla.tar.gz
``` or ```
sudo chmod 664 .mozilla.tar.gz
```

---

### Post by nycste on 2008-07-15
> **smo0th said:**
> when browsing a directory with nautilus(system graphical file browser) you can see hidden files by pressing ctrl+h, 



you don't want to remove root permissions and you unhide a file by removing the '.' at the beginning of the file, like:
```
sudo mv .mozilla.tar.gz mozilla.tar.gz
```

if you want to set write permissions for you, change the file ownership with ```
sudo chown nycste .mozilla.tar.gz
``` or ```
sudo chmod 664 .mozilla.tar.gz
```

thanks man, this worked fine
sudo mv .mozilla.tar.gz mozilla.tar.gz

now i dont quite fully understand the changing permissions thing on the 2 lines u mentioned afterwards but the . before the name suggests hidden or root protected so now i know and understand that

how would i change a file without using the sudo mv command?
sudo nautilus 

which then gives me root power right and then i could simply right click go to properties and remove or remove the . before the name?

thanks

---

### Post by 00Davo on 2008-07-15
> **nycste said:**
> 

how would i change a file without using the sudo mv command?
sudo nautilus 

which then gives me root power right and then i could simply right click go to properties and remove or remove the . before the name?
thanks

sudo nautilus opens up a regular file browser as root, so you can indeed remove the . using it, provided you can use a file browser. ;)

---

### Post by smo0th on 2008-07-15
> **nycste said:**
> 
how would i change a file without using the sudo mv command?


if the file has root ownership you need to use sudo in order to have enough permissions to change it, be careful when using sudo and opening root file browsers like with sudo nautilus, you don't want to accidentally delete files or something like that :)

---

### Post by nycste on 2008-07-15
> **00Davo said:**
> sudo nautilus opens up a regular file browser as root, so you can indeed remove the . using it, provided you can use a file browser. ;)

got it thanks

> **smo0th said:**
> if the file has root ownership you need to use sudo in order to have enough permissions to change it, be careful when using sudo and opening root file browsers like with sudo nautilus, you don't want to accidentally delete files or something like that :)

gotcha, and yea i could imagine how easy it is to delete stuff

---

### Post by nycste on 2008-07-31
> **smo0th said:**
>  or ```
sudo chmod 664 .mozilla.tar.gz
```

can someone explain what the

chmod 664 stands for.. thx

mainly the number is in question, chmod i know is a command to control ownership or something i used it setting up nvidia drivers

---

### Post by linux_tech on 2008-07-31
chmod 664 filename gives the owner of the file read & write (4+2+0) permission, gives the group  read & write (4+2+0) permission, and gives the rest of the world read-only (4+0+0) permission

---

### Post by nycste on 2008-07-31
> **linux_tech said:**
> chmod 664 filename gives the owner of the file read & write (4+2+0) permission, gives the group  read & write (4+2+0) permission, and gives the rest of the world read-only (4+0+0) permission

wow thanks i would of never knew that lol its soo simple, yet so complex to the untrained eye

---

