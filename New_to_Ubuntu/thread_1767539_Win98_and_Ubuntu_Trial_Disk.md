---
title: "Win98 and Ubuntu Trial Disk"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by ICEhockeyGOALTENDER on 2011-05-25
My windows 98 computer is an ibm computer from long ago...I have many other (up to date) computers but i would like to know how to get to the boot menu in win98 system that i have so i can hopefully install ubuntu and live peacefully. One problem, i have no idea of the specs of that computer so i cant really tell anyone anything if they might need to know. all i know is that i want to install ubuntu v11.04 on my win98 computer. is such a thing possible? or would i have to go down to an older verion of ubuntu to get it on my win98 computer?     

Please help asap.
___________________

&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;, 
&#1057;&#1101;&#1084;

---

### Post by zealibib slaughter on 2011-05-25
I doubt ubuntu will run on a computer that old, you may want to try lubuntu instead.
To get to the boot menu try escape or one of the function keys at startup.

---

### Post by yeats on 2011-05-25
You'll probably need to discover the specs.  Here's a link that may help:

[http://www.computerhope.com/issues/ch000017.htm#01](http://www.computerhope.com/issues/ch000017.htm#01)

Without knowing those, I would guess that regular Ubuntu will be far too resource-intensive for your older computer.  I would try Lubuntu ([http://lubuntu.net/](http://lubuntu.net/)).  If not that, you could try something even lighter like Puppy Linux ([http://puppylinux.org/](http://puppylinux.org/)) which is based on (though not supported by) Ubuntu.

---

### Post by mikewhatever on 2011-05-25
I'd say that a 1998 computer is probably too old for any version of Ubuntu, and, in fact, any graphical installer. Perhaps Lubuntu will work though. Anyway, why do you have to 'get to the boot menu in win98 system' to install Ubuntu? Have you tried booting the Ubuntu CD? If yes, what happens.

---

### Post by ICEhockeyGOALTENDER on 2011-05-25
tryed booting it and there is no boot menu dedicated key to acess the boot menu
 
my specs are 
------------------
System Information
------------------
   Operating System: Windows 98 (4.10, Build 2222)  A 
           Language: English (Regional Setting: English)
System Manufacturer: n/a
       System Model: n/a
               BIOS: n/a
          Processor: Intel(R) Pentium(R) 4 CPU 1.60GHz
             Memory: 254MB RAM
          Page File: 114MB used, 657MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 4.09.0000.0904 32bit
------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: The file ialmdrv.drv is not digitally signed, which means that it has not been tested by Microsoft's Windows Hardware Quality Labs (WHQL).  Current drivers tested for a WHQL logo are only available on Windows ME, Windows 2000, and Windows XP.  New Windows 98 drivers are no longer tested for WHQL logos.
        Sound Tab 1: No problems found.
          Music Tab: No problems found.
          Input Tab: No problems found.
        Network Tab: No problems found.
--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (n/a)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (n/a)
DirectMusic: 0/5 (n/a)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)

---

### Post by dFlyer on 2011-05-25
Min memory requirements is 384 to run 11.04, your system has 254 so you'll have to upgrade your ram before trying 11.04.

---

### Post by yeats on 2011-05-25
If you want to give Lubuntu a go, I would consider installing with the Minimal Ubuntu installer:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

once that's installed, you can do:

```
sudo apt-get install lubuntu-core
```  

which would be a minimal Lubuntu installation that you can add programs from there.

> tryed booting it and there is no boot menu dedicated key to acess the boot menu

You may need to go into your computer's BIOS settings and set it to boot from CD (or hopefully USB, but if it's that old, USB boot may not be possible).

---

### Post by nerdy_kid on 2011-05-25
yeah, there is no possible way 11.04 is going to run on that.  I'd try DSL or slitaz.  Maybe Lubuntu, but idk.

---

### Post by L a r r y on 2011-05-25
> **nerdy_kid said:**
> "Microsoft Windows: A collection of 32bit extensions and a graphical shell for a 16bit patch to an 8bit O.S. originally coded for a 4bit microprocessor written by a 2bit company who cant stand 1 bit of competition." Jargon File 4.4.7 

Like your signature!

---

### Post by Mark Phelps on 2011-05-26
Second the advice to avoid Ubuntu for your PC.  It's not the age that's the problem; it's the lack of resources, especially the small amount of system memory.

I have an old laptop of similar specs, and even when I tried to load Ubuntu 8.04, it would not run at a decent speed and would only display 800x600.

---

### Post by mastablasta on 2011-05-26
there is no data on graphics card. however this computer CAN handle Ubuntu (at least 10.04 LTS version) - only it will be kind of slow when opening the applications, but otherwise just fine. It also depends on programmes you will be running. basic system will use about 120-130 MB RAM. you will need to adjust some settings to get it low like that.
 
I suggest you give Lubuntu 11.04 a try. There is no need for minimal ISO. Graphical install should work just fine. you shoudl also be able to try it without installing by booting from CD. Lubuntu needs about 90-110 MB ram to run the OS the rest you can fill with some light weight applications. 
 
what i am worried here is your graphics card. if you have one of those early intel chips then you migth be dissaointed as the support for them in linux is not as good.
 
since you don't have any boot key menu you need to go to BIOS setup and change the boot order there so that computer first check the CD (boots from CD) and then if it doesn't find anything in there it goes to hard disk.
 
good luck. and if you can get some second hand RAM sick that fits in you maschine (maybe for free) and if computer nmotherboard can take it you could upgrade to 512 MB and it will all be a lot more faster.

---

### Post by jtarin on 2011-05-26
Try Slackware......it will run on that. A steeper learning curve than Ubuntu.
> Slackware Overview
Slackware Linux is a complete 32-bit multitasking "UNIX-like" system. It's currently based around the 2.6 Linux kernel series and the GNU C Library version 2.7 (libc6). It contains an easy to use installation program, extensive online documentation, and a menu-driven package system. A full installation gives you the X Window System, C/C++ development environments, Perl, networking utilities, a mail server, a news server, a web server, an ftp server, the GNU Image Manipulation Program, Mozilla Firefox, plus many more programs. Slackware Linux can run on 486 systems all the way up to the latest x86 machines (but uses -mcpu=i686 optimization for best performance on i686-class machines like the P3, P4, Duron/Athlon, and the latest multi-core x86 CPUs). 

---

### Post by nerdy_kid on 2011-05-26
> **L a r r y said:**
> Like your signature!

:D  thanks!  :guitar:

---

