---
title: "Ndiswrapper-utils:  WTF is lib6? Dependency not satisfiable?"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Helpmeplz on 2007-09-15
This is what I got after trying to install ndiswrapper-utils-1.9 : 
"Package: ndiswrapper-utils-1.9

        Error: Dependency not satisfiable: lib6
Status:"


I installed ndiswrapper-common fine.... helpmeplz?

---

### Post by FlyingIsFun1217 on 2007-09-17
Bump.

Can't figure out this one... :/

FlyingIsFun1217

---

### Post by nixfedex on 2007-09-17
If you are using apt-get can you post the entire commands you typed and the response you got? It will help in debugging...

---

### Post by kevdog on 2007-09-17
do this 

sudo aptitude install build-essential

---

### Post by Helpmeplz on 2007-09-18
hey, umm i will try that but I don't have a working internet connection, so i downloaded the .deb's from the archive... i couldn't use apt-get

---

### Post by kevdog on 2007-09-19
You can do that, but for no working internet connection but you do have an install cd

With CD rom in drive
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential linux-headers-`uname -r`

Those are backticks and not quotes

---

### Post by Helpmeplz on 2007-09-20
Well, I boot up my desktop from my hard drive, insert the CD, do "sudo apt-cdrom add" and it does a few lines of text and says "E: CD is unmountable." What???

And also...do i actually put "uname" or my username?

---

### Post by kevdog on 2007-09-20
Just type uname -r at the command line and you will see what the output is.  If the cd is unmountable is the cd readable -- this might be a problem.

---

### Post by Helpmeplz on 2007-09-21
The CD is readable; I installed Linux from it! I DLed it, not ordered it, and used InfraRecorder.

---

