---
title: "No such file or directory"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by linux dummy on 2009-03-05
Hi

I cannot understand why I cannot access my home directory 'stephen' at the command line.  I originally loaded ubuntu server (first time using linux) and wanted to load a GUI just to see the structure of a linux system.  I managed to extract the openbox tarball from a CD into a directory (openbox) but could not get into the directory to start the install.  I could change the name and permissions, and even delete it.
this was in home$, as was my home directory stephen$.  So I have now loaded ubuntu desktop.  At the GUI I can access stephen$ and see subdirectories.
So I tried again using Terminal, and cannot get into stephen$
The listing is shown below. I cannot work this out. 

stephen@stephen-desktop:~$ cd /home
stephen@stephen-desktop:/home$ ls -l
total 4
drwxr-xr-x 29 stephen stephen 4096 2009-03-05 23:54 stephen
stephen@stephen-desktop:/home$ cd /stephen
bash: cd: /stephen: No such file or directory
stephen@stephen-desktop:/home$ 

regards

---

### Post by bodhi.zazen on 2009-03-05
it is the leadin /

so

cd stephen

The difference between relative and absolute path

relative = relative to current directory == cd stephen
absolute = start with / == /home/stephen

You can jus t

cd 

with no arguments, that will go home

Or
 
cd ~

~ is short for $HOME which is an environmental variable for /home/stephen :twisted:

You can go to another users $HOME with 

cd ~user

---

### Post by linux dummy on 2009-03-05
Got it. Thanks for that, that hasn't been obvious from the books I've read.  I needed to read your post a few times to fully get it.

Many thanks

---

