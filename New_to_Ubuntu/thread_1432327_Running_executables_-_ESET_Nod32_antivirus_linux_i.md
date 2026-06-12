---
title: "Running executables - ESET Nod32 antivirus linux install"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by seemore on 2010-03-17
I sold vista and now only use ubuntu 9.10 since yesterday and it feels great.

I was trying to install an antivirus (ESET NOD32), I downloaded the linux version from: [http://http://beta.eset.com/linux]("http://http//beta.eset.com/linux") , so now I have the file ueav.i386.linux and it is an executable type file. When I try to open it with archive manager I am informed that archive manager "no comprehende". How can I open this file?

---

### Post by wjm on 2010-03-17
> 
chmod +x ueav.i386.linux
sudo sh ./ueav.i386.linux
Should work but I'm on a system with SELinux and it doesn't seem to like that so I can't actually tell you if that's 100% it.

---

### Post by seemore on 2010-03-17
> seymour@Box9:~$ chmod +x ueav.1386.linux
chmod: cannot access `ueav.1386.linux': No such file or directory
seymour@Box9:~$ sudo sh./ueav.i386.linux
[sudo] password for seymour: 
sudo: sh./ueav.i386.linux: command not found
seymour@Box9:~$ 


I gave it a shot and it came back with that^.

---

### Post by wjm on 2010-03-17
I shouldn't have been so literal - that's the name of the file on the website you linked, change it to reflect what you have on your system and try chmod/etc again.

---

### Post by llamabr on 2010-03-17
do a:

```
file ueavi368.linux
```

and post the output. I suspect it's not executable, or you didn't get it all.

---

### Post by seemore on 2010-03-17
llamabr: it said file not found.

wjm: how do you write directories in linux? I am used to using dos and windows. It is in home/seymour/downloads

---

### Post by llamabr on 2010-03-17
Sorry, I too should have been more explicit:

```
cd Downloads
file filename.linux
```

and post the output.  What you're doing there is cd (change directory) to the place that it is.  And then running the 'file' command, on the actual file.  The 'file' command tells you what kind of file it is.  For example, from my system:

```
brock@vader:~$ file Mountain\ Forest.mp3 
Mountain Forest.mp3: MPEG ADTS, layer III, v1, 128 kbps, 44.1 kHz, JntStereo
brock@vader:~$ 

```

---

### Post by oldsoundguy on 2010-03-17
NEW (not really) WAY folks.
Put the downloaded file on your desktop.
Right click
properties
select GRANT PERMISSIONS (all of them)
close
double click on the file (sometimes a single click will do)
it should install if it is a .deb file

No more terminal and chmod 777 or whatever!

---

### Post by llamabr on 2010-03-17
> **oldsoundguy said:**
> 
it should install if it is a .deb file

No more terminal and chmod 777 or whatever!

Uh, huh.  And if it doesn't, open a terminal, and find out what kind of file it is.  Either you got the wrong thing, you didn't get the entire thing, or it's not set executable.

---

### Post by seemore on 2010-03-17
Putting it on the desktop and changing the permissions worked! Thanks for all of your help guys, I am loving ubuntu, this was the one problem (oh and the ipod) I couldn't workout by myself yet.

Thanks for a warm and such a civil tone on an internet forum, who would have thought?

I've even managed to get MSoffice 2007 working in the first 24 hours. That was my only issue with getting rid of vista and now it is gone forever! I am spreading the word.

---

### Post by madmoonfish on 2010-04-04
I used

user@laptop:~/Downloads$ chmod +x ueav.i386.linux

user@laptop:~/Downloads$ ./ueav.i386.linux


installed fine with me with license till June :)

---

### Post by JCyberinux on 2010-09-01
hi guys!, sorry to bump in to this thread, but i have a question not regarding on installation.

can i know if theres a command line to scan a selected drives, folders, usb, etc. ? thanks!

---

### Post by fik_tau on 2010-10-16
I used ubuntu 9.10 on my Amd Phenom X4 and just succesfull to install eset NOD32 (ueav.i386.en.linux) with help from tihis forums. Thank's very much.

---

