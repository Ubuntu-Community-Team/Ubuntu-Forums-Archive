---
title: "Update manager error"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by valid trust on 2011-06-30
my update manager is not working correctly
this error keeps popping up when i try to update:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by dFlyer on 2011-06-30
Appear to be a type-o:

/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages, E:The package lists or status file could not be parsed or opened.'

It should read:

/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages

---

### Post by valid trust on 2011-06-30
so how would i go about reporting the error and fixing the problem in terminal? I am very new to ubuntu.

---

### Post by jerrrys on 2011-06-30
also rubi1200's answer seems to work

[http://ubuntuforums.org/showthread.php?p=10985675#post10985675](http://ubuntuforums.org/showthread.php?p=10985675#post10985675)

---

### Post by wildmanne39 on 2011-06-30
Never mind the text will not format correctly.
[SIZE=4][/SIZE]

---

### Post by wildmanne39 on 2011-06-30
Hi, ok I think I got my format problem fixed so here is the commands to fix your update problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.

---

### Post by SniperWolf13 on 2011-06-30
> **valid trust said:**
> so how would i go about reporting the error and fixing the problem in terminal? I am very new to ubuntu.

Hi there,

I'm a bit new myself, but the typo thing mentioned before is a really, REALLY good point! That gets me all the time too and I get error messages or the commands in Kosole just won't work and I think they're right. A second look later and I facepalm and in that D'oh moment realize I have switched two characters, forgot a - or a / or something silly. 

Konsole is a tough place if you're in a hurry, or just a wee bit dyslexic. This happens to me a lot and it's just one of those things I'm getting used to. The overall rewards of playing around with Linux at both the GUI and Konsole are so very worth it. 

Don't worry, you'll just start now and in a month or two, you'll be building networks with multiple servers! It doesn't take very long to get a feel for it.

---

