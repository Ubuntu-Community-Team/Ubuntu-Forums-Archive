---
title: "No GUI in Ubuntu 10.10 fresh installation"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by X-Treme on 2011-02-03
Hello everyone. This is my first date with Ubuntu :p. 
Mine is an old system with P4 and the motherboard is P4VM800M7 with 1 GB RAM. No graphic cards. ;).

I downloaded Ubuntu 10.10 desktop amd64 and used UNETBOOTIN to make a bootable USB off it and went on with the installation.

Actually mine is a dual boot - WINDOWS 7 and Ubuntu 10.10
Everything went fine and on restarting after the installation got over and booting up ubuntu, i was greeted with COMMAND LINE INTERFACE :mad:. Tried the following 

**sudo service stop gdm**
No such service as stop

**startx**
Fatal Error - No screens found

**/var/log/Xorg.0.log**
Permission denied

**lspci | grep VGA**
01.00.0 VGA compatible controller. VIA Technologies, Inc KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

**sudo apt-get install gnome-desktop**
gnome-desktop already installed and is up to date

I would very much like to go on with ubuntu and explore that which would be a breeze with the presence of a GUI. So any help to bring it p will be appreciated very much

PS - My system runs WINDOWS 7 without a glitch

---

### Post by raydeen on 2011-02-03
One thing I would try is downloading the 32 bit x86 .iso. You have an Intel motherboard (and I'm assuming a 32 bit chip) and you're trying to use a 64 bit AMD version of Ubuntu. It could be that there's enough of a difference that your video hardware isn't being detected properly.

---

### Post by X-Treme on 2011-02-03
Actually i did download Kubuntu 10.10 x86 first and installed. The story was same even then, got struck with CLI. 

As to the processor architecture i am pretty sure that it is x64 capable because SecurAble (an app for windows which gives info on the processor) says so. If my processor is not x64, then even ubuntu 10.10 x64 should not have gotten installed right? For me it has just gotten struck in the CLI.

---

### Post by candtalan on 2011-02-03
Welcome!
If you are getting problems (sorry to hear that) then use 32 bit Ubuntu, (not kubuntu, not 64 bit) at least to start with, more things are likely to work without question and particularly, support responses are more likely to be useful.

Do you get a working system with the live usb?

If you still get display problems, consider nomodeset
[http://ohioloco.ubuntuforums.org/showthread.php?t=1496400](http://ohioloco.ubuntuforums.org/showthread.php?t=1496400)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by JKyleOKC on 2011-02-03
It sounds as if the X Window Server (that provides the ability to display graphics) isn't finding a driver for your S3 video, causing the system to fall back to text mode. Were it a 64 vs 32 bit problem, you normally would not get any response at all!

The most recent versions of Ubuntu have used a newer X server that does not depend on an /etc/X11/xorg.conf file at all, and so they do not create the file by default. However, these versions **WILL** use the file if it exists, so you can create it from the text mode login, and set it to use the "vesa" driver -- which is quite generic and should work after a fashion with almost all video chip sets. It won't have all the eye candy of a custom driver, but it will at least let you get started. A sample file that ought to work for you despite the post being for an older version of Ubuntu is at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and you can copy it from there. Scroll down to "Workaround B:" to find it.

EDIT: To view the log, use **less /var/log/Xorg.0.log** which will display it a page at a time; the space bar (or PgDn key) will get you the next page. Without "less" the system sees this as a command, rather than a request to display the log. In the log, look for lines that begin with EE indicating errors.

The **sudo service** command is **sudo service gdm stop**; you have the last two words transposed. 

Hope this helps! This video problem seems to account for almost half the traffic in this forum!

---

### Post by TechWiz2100 on 2011-02-03
I understand this isn't a 32/64bit issue but I do recommend the OP to switch to 32bit anyway because they have less than 4GB of RAM and the P4 is not a true dual core processor, its only hyperthreaded to seem like one.

As a result, the OP will probably get worse performance from the 64bit OS.

Just my 2 cents

---

### Post by sdowney717 on 2011-02-03
curious, what happens if you run the liveCD option?
yes, sounds like it is a video driver problem with the S3 chip.

in that Xorg.0.log log file, 'EE' will show any errors.

I would do what they say and setup an xorg.conf file to use the vesa driver

> Workaround B: Switch to -vesa

Paste the following into /etc/X11/xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by X-Treme on 2011-02-04
Guys, here is what happened.
The (EE) - Errors in Xorg.0.log are

[B](EE) Chrome(0) No valid modes found
(EE) Screen(s) found, but none have a usable configuration
Fatal error
No screen(s) found[/B]

After the closing log message i got 2 more lines
[B]Xinit : No such file or directory (errno 2) : unable to connect to X server
Xinit : No such process (errno 3) : server error[/B]

As to Xorg.conf file, i opened it using the vi command and i did enter everything and when i tried to save it using :wq , an error message flashed saying that **Xorg.conf cannot be opened to be written **

---

### Post by X-Treme on 2011-02-04
Regarding to the live cd option, it runs well and i get the GUI in that.       

I even tried installing it inside windows using virtualbox and it turned out to be fine. GUI came up without any problem at all. It was rather slow though, owing to my 1 GB RAM

I also have the iso of Ubuntu 10.10 alternate install x32. Should i give it a go?

---

### Post by JKyleOKC on 2011-02-04
> **X-Treme said:**
> 
As to Xorg.conf file, i opened it using the vi command and i did enter everything and when i tried to save it using :wq , an error message flashed saying that **Xorg.conf cannot be opened to be written **Try it with **sudo vi /etc/X11/Xorg.conf** which should work. The files in /etc almost all require root permission to write, although most of them allow reading by anyone.

---

### Post by X-Treme on 2011-02-04
Yeah,just tried it and was able to create the file and fill it. But it didnt do any difference at all. The same old CLI comes up!!!

---

### Post by X-Treme on 2011-02-04
Removed all earlier installations
Tried 9.04 - Got the same problem 
Tried 8.10 - Worked out. :-)

---

### Post by JKyleOKC on 2011-02-04
Yep, that's where they changed to the newer version of the X Window server. Still, since they're no longer doing security updates to 8.10, you'll need to solve the driver problem. Even if you drop back to 8.04, it will only get the updates through this coming April...

---

### Post by X-Treme on 2011-02-04
oh! Better i will install 8.04. 
Thank you all for your support :-)

---

### Post by XAD6 on 2011-04-17
hello everyone 

Just want to say thank you [JKyleOKC]("http://ubuntuforums.org/member.php?u=374258") 

you gave plenty of great information

---

