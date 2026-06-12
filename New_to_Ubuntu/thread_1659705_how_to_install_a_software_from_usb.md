---
title: "how to install a software from usb"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by suryak on 2011-01-04
I have a software that has to be install for my USB modem.. 
so I looked into readme file of it to know how to install..
the very first few goes this way .. 
" --How to Install---------------------- 
*You need login as root* 
1. Run "install" in TERMINAL to install MobilePartner 
   eg: # bash /<path>/install "

i could able to login as root be entering " sudo su " in terminal 
but I'm not able to further..
It's saying " no such file/ directory "..
I tried to enter the code .. in many combination leaving <. > with them and a lot .. but unable to do it...

how to do it ?
can you explain me ??

---

### Post by TeoBigusGeekus on 2011-01-04
Where is the install file located?
You should navigate to it's location with the cd command and execute it from there.

PS: Don't tell me you've literally entered bash /<path>/install in your terminal...:p

---

### Post by seawolf167 on 2011-01-04
If your USB modem is anything like the ones I've used, my guess is that the USB modem contains software on it that you need to install (essentially just the drivers & software suite).

So, when you plug in the USB modem, Ubuntu should automatically mount it as a USB device (I think the default place is now /media/device_name)

So you'll need to change to root

```
sudo su
```

Then browse to the location of the software/drivers contained on the USB modem

```
cd /path/to/USB/modem
```

Then you'll need to install whatever it wants you too (maybe its a tar.gz or tar.bz2, or a .run, .deb, etc.). If you post the contents of the USB modem (or the file name from the README.txt that should exist we can help with the commands to install whatever file type it is)

List directory contents (of your working directory)

```
ls
```

---

### Post by Chronon on 2011-01-04
You need to navigate to the right directory or just give the path to the install script.  It's probably safest to navigate to the directory, ensure the presence of the install script with "ls", then run it by doing
```
./install
```

(you might need to make sure that "install" is executable)

---

### Post by howefield on 2011-01-04
Duplicate threads merged, as both had replies.

---

