---
title: "Totem, VLC crashes and no desk top effects"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by Yerushalmy on 2009-09-24
hey

I am pretty new to Linux, and every time I try to watch a movie on Totem it crashes, I installed VLC and the same problem occured. In addition I can not have any desk top effects. Do you know anything that might be able to help me?

---

### Post by Nozze on 2009-09-24
Sounds like a graphic driver issue.
witch kind of graphic card and driver do you use?

---

### Post by Hallvor on 2009-09-24
> **Yerushalmy said:**
> hey

I am pretty new to Linux, and every time I try to watch a movie on Totem it crashes, I installed VLC and the same problem occured. In addition I can not have any desk top effects. Do you know anything that might be able to help me?

It might help if you launch Totem or VLC from the terminal. You can launch it with ```
totem
```or ```
vlc
``` You will then get some text output in the terminal if they crash. Post the output here afterwards.

---

### Post by superprash2003 on 2009-09-24
try looking under system->admin->hardware drivers for any restricted drivers..

---

### Post by khelben1979 on 2009-09-24
```
sudo lspci
```
to give us some information about your hardware.

---

### Post by Yerushalmy on 2009-09-25
I am going to sound like an idiot because I do not know where to see my hardware but what I can tell you is that it is an HP

Intel (R) pentium (R) 4CPU 3 GHz

I am not to sure if that makes much of a difference, do I need to open my box to see the kind of hardware it is....I am new to Linux, only started using it on Thursday

---

### Post by keiichidono on 2009-09-25
No problem buddy, we'll help you through this. ;) Don;'t open your machine! In the top left hand corner of your screen, there's a menu that says "Applications", the first menu item there is "Accessories", in that menu there will be a menu item called "Terminal" so click that and you'll see a window that looks kind of creepy. Don't freak out. Use your keyboard and carefully type in "sudo lspci" without the quotes and enter your password when it asks you to. Then either take a screenshot or tell us what you see.

---

### Post by Yerushalmy on 2009-09-25
every time i type sudo lipsci in it asks for my password but it does not allow me to type anything. I am not sure why haha

---

### Post by Yerushalmy on 2009-09-25
*lspci

---

### Post by khelben1979 on 2009-09-25
> **Yerushalmy said:**
> *lspci

Okay, and can you cut and paste the text into this thread?

---

### Post by Yerushalmy on 2009-09-25
okay something different happened now

david@david-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
david@david-desktop:~$

---

### Post by khelben1979 on 2009-09-25
I see you have integrated graphics. Interesting. This means that you don't need to download any graphic drivers since they are in your Linux kernel.

I suggest you add [Medibuntu]("http://en.wikipedia.org/wiki/Medibuntu") to your system. [Read here]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") how to do it.

One other thing can be that the Linux kernel just don't like your hardware, but let's look into that later.

---

### Post by Yerushalmy on 2009-09-25
every time i type sudo lspci in my system it asks for a password but does not let me type anything so i can't do anything that involves that...is there any solution to this problem because on windows i could watch movies and use everything? I really prefer linux so is there a way to get it to work?

---

### Post by Yerushalmy on 2009-09-25
now my screen savers do not work, none of them

---

### Post by clive littlewood on 2009-09-25
Hi

When you type your password the letters DO NOT appear on the screen for security.

Just type them as normal and press enter.

Clive

---

### Post by Yerushalmy on 2009-09-25
oh really, thank you so much :)
It's been driving me mad

---

### Post by Yerushalmy on 2009-09-25
this is what my pc uses

david@david-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by galilio on 2009-10-01
**[click here to know more]("http://www.google.com")**:)

---

### Post by GO%)$@*1 on 2009-10-14
> **Yerushalmy said:**
> every time i type sudo lipsci in it asks for my password but it does not allow me to type anything. I am not sure why haha
It looks like you are not typing anything BUT it is recieving input. The letters are blocked for privacy.

---

### Post by pony on 2009-10-19
I still have quite a bit to learn about computers. I have used the terminal quite a bit though. I know when you type a command in the terminal it asks you for your password. Then you type your password in and press enter. If you done something wrong then the terminal will ask you to type it again. This may be your case. Just try a command and type your password even though it won't show up and press enter. If that doesn't work I don't know what will.

---

### Post by kesman on 2010-10-29
> **Yerushalmy said:**
> 
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

This is your graphics adapter, an integrated one.
What version of Ubuntu are you running? Have you done all the system updates, it might be some bug in outdated packages, so run this in terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
it will ask your password, and if updates are found, it will ask your confirmation to install them. Might be hundreds of megabytes, so be prepared to wait a little, depending on your internet bandwidth.
Post here if any problems occur. Cheers!

---

### Post by Lektorvis on 2010-12-13
Stefan Glasenhardt is working on an Intel i8xx driver.

You should add his repositories to your software sources.
[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/~glasen/+archive/intel-driver")


When done you open Synaptic and get the 

"xserver-xorg-video-intel" 
"libdrm-intel1"
 
The problem may still persist after update though, (I got it myself on my old Acer laptop) but Glasen might come up with a full working driver in the future.

---

