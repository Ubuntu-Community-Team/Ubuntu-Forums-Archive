---
title: "Can not get to GUI when trying out Ubuntu 10.10 from live CD"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Jos Visser on 2010-12-29
I fail to get Ubuntu 10.10 on screen from live CD

I set BIOS to boot from CD. After reboot I get Ubuntu icon with 5 dots underneath which blink consecutively at first. Then a colourful screen appears. After that the welcome/install screen with the 'Try Ubuntu / Install Ubuntu' option. I choose 'Try Ubuntu', Ubuntu starts loading but ends with a complete black screen. After a few seconds the mouse pointer appears which can be moved around. But no further action - even after having lunch. No further blinking lights on the computer.   

By chance I pressed Contr/Alt/F1 and got to what appears to be a Ubuntu terminal with a 'ubuntu@ubuntu:~$' prompt. From there I could enter your 'lspci' command to get some system information listed below.

With Windows I verified the integrity of the downloaded 'ubuntu-10.10-desktop-i386.iso' file with MD5 installed from Cygwin. I also verified the live CD with the same program.

I have never used any Linux or Ubuntu but have read a lot about Ubuntu.

My system :

Maxtor IDE hard drive 250GB with one partition only
Intel Pentium4 3.06GHz
Foxconn motherboard
RAM 1 GB
Windows XP SP3
Samsung DVD writer
VGA controller : ATI Technologies Inc RV515 (Radion 1300)
Display controller : Same as above with '(Secondary)' added at end.

Thanks for your help. You will appreciate my reservation on Ubuntu if trying it out does not even work

---

### Post by audiomick on 2010-12-29
HI. Sounds like Ubuntu is having trouble with your graphics card. That is not very common these days, but still happens occasionally :(

The thing that you mention that
>  appears to be a Ubuntu terminal with a 'ubuntu@ubuntu:~$' prompt.
is the system running without a GUI, i.e. with no graphical desktop.

There is likely to be a way to get Ubuntu running despite this, but I am afraid that is beyond the bounds of my knowledge, sorry. Hopefully someone else will post who can be more helpful.

---

### Post by sparker1 on 2010-12-29
Hi Jos,
 
I'm a noob but I did have a similar experience. If your problem is the same as mine (nvidia graphics but your card could have problems too) then when you get to the selection screen press F6 for options and choose "nomodeset". Then select  "try Ubuntu without installing".
If my suggestion works and you decide to install ubuntu choose the same option. You may then find you won't get to the login screen. In that case this thread will help 
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785)
 
The post by davidryderuk is the part that helped me.

---

### Post by Jos Visser on 2010-12-30
Thanks Sparker1. I owe you one (pint or liter?). You must press the F6 key before you get to the welcome/installation screen.  But Linux/Ubuntu must surely perform better. They cant expect you to buy a car that wont start when you turn the key. Even if you get it free it wont take you to point B. Switch to Linux? - in no hurry after this.

---

### Post by sparker1 on 2010-12-30
Great news. I'll have a litre since a litre is bigger than a pint.

---

