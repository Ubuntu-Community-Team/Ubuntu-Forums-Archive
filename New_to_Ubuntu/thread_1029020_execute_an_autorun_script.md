---
title: "execute an autorun script"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by stanjest on 2009-01-03
How do you execute an autorun script?
I was trying to install a printer driver in UBUNTU 8.04.
The driver was a tar zip file which I have extracted.
The content was an autorun script and a Linux sub directory with all the files in it. 
It will have to be done as root user.

---

### Post by handydan918 on 2009-01-03
If you can provide the exact filename, perhaps someone can figure this out for you.

---

### Post by ubrox on 2009-01-03
Can you give a link to the download of the tar file? 

Autoconf scripts are generally named "configure". You just have to start it like:

shellprompt> ./configure  <and give the options here, if any>

---

### Post by cariboo on 2009-01-03
What make and model of printer is it that you are trying to install, most printers but Lexmark and Canon, are setup automatically when you use the Printing Wizard. Go to System-->Administration-->Printing and just follow the prompt.

Jim

---

### Post by jamesrl on 2009-01-03
First extract the tar-ball.   Say its called printer.tar.gz 
From the terminal (cd to the proper directory) type;

```
tar xvfz printer.tar.gz
cd printer
ls -l

```
(first extract the tarball, then change directory to where it was just extracted (probably printer or name of the tarball), and then you look inside with ls -l.)

If you see a file called configure, you probably have to do
```
./configure
make
sudo make install

```
If you see an executable named say autorun or autorun.sh or autorun.bin or similar (its an executable if the privileges part has an x in them like -rwxr-xr-x ) then you need to type
```
sudo ./autorun.sh
``` (replacing autorun.sh with whatever its named).

---

### Post by stanjest on 2009-01-03
Thanks. That was it.

---

