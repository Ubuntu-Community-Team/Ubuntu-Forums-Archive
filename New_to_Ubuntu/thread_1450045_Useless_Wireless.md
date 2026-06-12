---
title: "Useless Wireless"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Thunder X on 2010-04-08
[SIZE=4]before installing ubuntu, i'm reading how simple it is, how simple everything is. well here i am trying to perform a ridiculously simple task, and i can't seem to get it done. why can i not just simply connect to my wireless connection? ubuntu does not "see" my connection, and that "connect to hidden network" thingamajig (or whatever it's called) doesn't do anything. i'm also looking at all the forum threads here and all i see are lines of code that i don't understand. why is it so difficult to get some wireless satisfaction???[/SIZE] :confused:

---

### Post by anewguy on 2010-04-08
It isn't.  In Windows, drivers are installed for devices to work.  Linux is no different, except that a vast majority of manufacturers don't create things for Linux.  So, in order to help, we need you to do 2 things for us:

- open a terminal window (Click Applications, then scroll down to Accessories and then over and down to Terminal and click)

- at the prompt:

type:

lspci <press enter>

if this is a USB adapter or if the computer is a laptop, please also type:

lsusb <press enter>

Copy the output of both of these back here so we can see the chipset your adapter is using and guide you from there.

Dave  ;)

---

### Post by kapi on 2010-04-08
This may be of assistance or Not.

When I first switched to Ubuntu I had exactly the same problem and comments so don't stress - you've made the right move.

When first installing ubuntu 18 months ago i was informed that for the wireless to work after the successful installation you need to reboot and everything should work. It's as simple as turning on your wireless and then right clicking on the wireless icon (top right of nav bar). select enable wirless and then you should after a few second see the available wireless signals for you to logon to.

Hope this helps

---

### Post by Thunder X on 2010-04-08
> **anewguy said:**
> It isn't.  In Windows, drivers are installed for devices to work.  Linux is no different, except that a vast majority of manufacturers don't create things for Linux.  So, in order to help, we need you to do 2 things for us:

- open a terminal window (Click Applications, then scroll down to Accessories and then over and down to Terminal and click)

- at the prompt:

type:

lspci <press enter>

if this is a USB adapter or if the computer is a laptop, please also type:

lsusb <press enter>

Copy the output of both of these back here so we can see the chipset your adapter is using and guide you from there.

Dave  ;)

well, it would help if i knew how to copy and paste from one os to another. lol i did just as you asked, but can't copy from there to here (wxp). is there a way to do that? perhaps a minor magic spell?

---

### Post by Thunder X on 2010-04-08
> **kapi said:**
> This may be of assistance or Not.

When I first switched to Ubuntu I had exactly the same problem and comments so don't stress - you've made the right move.

When first installing ubuntu 18 months ago i was informed that for the wireless to work after the successful installation you need to reboot and everything should work. It's as simple as turning on your wireless and then right clicking on the wireless icon (top right of nav bar). select enable wirless and then you should after a few second see the available wireless signals for you to logon to.

Hope this helps

thanx kapi, but i've rebooted more times than i care to count. your assistance is appreciated nevertheless.

---

### Post by albert s on 2010-04-08
if you can write you could always write the commands down and then type them in.
have you tried a hard wired set up yet?
this I have found will usually sort out the majority of problems by automatically up dating and downloading the latest drivers.

---

### Post by x C0MMAND0 x on 2010-04-08
Go to System > Administration > Hardware Drivers 

See if there is anything there.  Also, if you want to post the output of your code you could always save it to a text file, then save it to a USB thumb drive and open it in Windows, or if you can hook in a hard line ethernet cable to your computer you can post on the forums.

---

### Post by Thunder X on 2010-04-08
> **anewguy said:**
> It isn't.  In Windows, drivers are installed for devices to work.  Linux is no different, except that a vast majority of manufacturers don't create things for Linux.  So, in order to help, we need you to do 2 things for us:

- open a terminal window (Click Applications, then scroll down to Accessories and then over and down to Terminal and click)

- at the prompt:

type:

lspci <press enter>

if this is a USB adapter or if the computer is a laptop, please also type:

lsusb <press enter>

Copy the output of both of these back here so we can see the chipset your adapter is using and guide you from there.

Dave  ;)

ok. here goes the info:

	 	 thunderx@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)  
 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)  
 00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)  
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)  
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)  
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)  
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)  
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)  
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)  
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)  
 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)  
 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller  
 03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)  
 03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)  
 03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)  
 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)  
 thunderx@ubuntu:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 thunderx@ubuntu:~$

---

### Post by Holyjoely on 2010-04-08
Take a look at the following thread and see if it helps you at all

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by Thunder X on 2010-04-08
> **Holyjoely said:**
> Take a look at the following thread and see if it helps you at all

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

thanx Holeyjoely, but i am afraid that all of the directions given there are more than i am capable of executing.

---

### Post by Thunder X on 2010-04-08
> **x C0MMAND0 x said:**
> Go to System > Administration > Hardware Drivers 

See if there is anything there.  Also, if you want to post the output of your code you could always save it to a text file, then save it to a USB thumb drive and open it in Windows, or if you can hook in a hard line ethernet cable to your computer you can post on the forums.

the former i will take a look at, the latter came in handy. thanx xCOMMANDOx

---

### Post by taylo31 on 2010-04-08
> **Thunder X said:**
> the former i will take a look at, the latter came in handy. thanx xCOMMANDOx

Hi All
I'm also new to ubuntu forum, but my hp pc hard drive crashed, and I installed a new one, but ms wanted to charge another 95 pounds to re-establish windows xp. anyway i've ordered and received the ubuntu cd, installed a fresh install from scratch, but i use a bt 1055 voyager usb stick for my wireless conection to the bt home hub 2.0, so can someone explain what i need to to do to get my wireless usb working.

Thanks

bob

---

### Post by egalvan on 2010-04-08
> **Holyjoely said:**
> Take a look at the following thread and see if it helps you at all

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

Good link, with good info, but it's pushing two years old.
Hardy was current back then.
Linux has matured tremendously in that time.
(I just installed Lucid on an old laptop (IBM TP41P) that had troubles with Hardy (no wireless, bluetooth or audio, bad video, etc)
EVERYTHING ran out-of-box... Wired/Wireless - Bluetooth / video/audio
EVERYTHING.)

Linux has matured.

(yes, sadly many hardware vendors refuse to support Linux. That is not Linux's fault)

So,
The OP has Broadcom chips for his wired/wireless LAN.

Broadcom has rather good support in up-to-date kernels...

**Thunder X**, please run this in a terminal so we can see what version of Ubuntu and kernel you have.

```
uname -a
```

---

### Post by coffeecat on 2010-04-08
@ Thunder X, you have a wireless chipset that licensing issues prevent the firmware from being included in a default install.

> **Thunder X said:**
> 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 

Have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrib%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrib%20drivers")

There is more on that page than you need. So - if you can connect with an ethernet connection, start from the heading "Internet Access" and follow steps 1 and 2.

If you can't connect with ethernet, then you can install the bcmwl-kernel-source package from the live CD. Go to the heading "No internet access" and follow steps 1 and 2 under that heading.

It is really quite straightforward. No terminal commands are necessary. You can do everything with the Synaptic package manager (System > Administration > Synaptic).

---

### Post by Holyjoely on 2010-04-08
> **egalvan said:**
> Good link, with good info, but it's pushing two years old.
Hardy was current back then.
Linux has matured tremendously in that time.
(I just installed Lucid on an old laptop (IBM TP41P) that had troubles with Hardy (no wireless, bluetooth or audio, bad video, etc)
EVERYTHING ran out-of-box... Wired/Wireless - Bluetooth / video/audio
EVERYTHING.)

Linux has matured.

(yes, sadly many hardware vendors refuse to support Linux. That is not Linux's fault)

So,
The OP has Broadcom chips for his wired/wireless LAN.

Broadcom has rather good support in up-to-date kernels...

**Thunder X**, please run this in a terminal so we can see what version of Ubuntu and kernel you have.

```
uname -a
```


Yeah, I was thinking 2008 wasn't that long ago. Hard to believe it is two years. Anyway, my Broadcom card worked as soon as I installed bcmwl-kernel-source from the Live CD, mentioned above. If that doesn't fix your problem then I'm out of ideas.

---

### Post by Thunder X on 2010-04-08
> **Holyjoely said:**
> Yeah, I was thinking 2008 wasn't that long ago. Hard to believe it is two years. Anyway, my Broadcom card worked as soon as I installed bcmwl-kernel-source from the Live CD, mentioned above. If that doesn't fix your problem then I'm out of ideas.

ok. i followed xCx advice re drivers. i received this message:

"no proprietary drivers are in use on this system" don't know what that means, but it doesn't sound good.

egalvan, when you say run this in a terminal, what does that mean please?

---

### Post by grifonas on 2010-04-08
> **Thunder X said:**
>  egalvan, when you say run this in a terminal, what does that mean please?

It means that you need to click on the menu entry called "Terminal" in Applications>Accessories>Terminal, and then type in the command there.

---

### Post by Thunder X on 2010-04-08
> **grifonas said:**
> It means that you need to click on the menu entry called "Terminal" in Applications>Accessories>Terminal, and then type in the command there.

thanx grifonas. i hate this side of the internet. on the other side, i'm pretty brilliant, but i'm a moron in offline mode. lol

---

### Post by Thunder X on 2010-04-08
> **Holyjoely said:**
> Yeah, I was thinking 2008 wasn't that long ago. Hard to believe it is two years. Anyway, my Broadcom card worked as soon as I installed bcmwl-kernel-source from the Live CD, mentioned above. If that doesn't fix your problem then I'm out of ideas.


here is the response when i entered the code:

	 	 thunderx@ubuntu:~$ uname -a  
 Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux  
 thunderx@ubuntu:~$  
 

make any sense?

---

### Post by durand on 2010-04-08
> **taylo31 said:**
> Hi All
I'm also new to ubuntu forum, but my hp pc hard drive crashed, and I installed a new one, but ms wanted to charge another 95 pounds to re-establish windows xp. anyway i've ordered and received the ubuntu cd, installed a fresh install from scratch, but i use a bt 1055 voyager usb stick for my wireless conection to the bt home hub 2.0, so can someone explain what i need to to do to get my wireless usb working.

Thanks

bob

I did a bit of research for you and it seems like a lot of people have managed to get that working. However, most of the solutions are a couple of years old so they might not be relevant anymore. Anyway, have you tried plugging it in and then rebooting? If that doesn't work, try using System > Administration > Hardware Drivers. There might be a driver for you. Finally, the last option, you might not like. It does seem to work for many people however.

[https://help.ubuntu.com/community/WifiDocs/Device/BT_Voyager_1055](https://help.ubuntu.com/community/WifiDocs/Device/BT_Voyager_1055)

You should probably start a new thread about this, rather than post in someone else's.

---

### Post by durand on 2010-04-08
> **Thunder X said:**
> here is the response when i entered the code:

	 	 thunderx@ubuntu:~$ uname -a  
 Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux  
 thunderx@ubuntu:~$  
 

make any sense?

It means that you are using a recent enough version of ubuntu for this to work. (ubuntu 2.6.31 is the kernel version which is in karmic, I think.)

Have you tried using this link? :[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrib%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrib%20drivers)

---

### Post by Thunder X on 2010-04-08
> **durand said:**
> I did a bit of research for you and it seems like a lot of people have managed to get that working. However, most of the solutions are a couple of years old so they might not be relevant anymore. Anyway, have you tried plugging it in and then rebooting? If that doesn't work, try using System > Administration > Hardware Drivers. There might be a driver for you. Finally, the last option, you might not like. It does seem to work for many people however.

[https://help.ubuntu.com/community/WifiDocs/Device/BT_Voyager_1055](https://help.ubuntu.com/community/WifiDocs/Device/BT_Voyager_1055)

You should probably start a new thread about this, rather than post in someone else's.

thanx durand. i'll take stab at it in the morn.

---

### Post by durand on 2010-04-08
Remember to look at the right post! One was for you, the other for taylo31.

---

### Post by hawaiian1der on 2010-04-08
This might be what your looking for:

> Put the installation disk into your drive

> Go to Software Sources
          > System
          > Administration
          > Software Sources

> On that very tab that it opens up to click, if your using Karmic Kola (9.10), the check box next to a blurb about the disk

> Close that window

> Open the Synapitc Package Manager
          > System
          > Administration
          > Synaptic

> Type in the letters "bcm" (Without the quotes)

> Click the box next to the words "bcmwl-kernal-source"
          > Click mark for installation

> Click yes to everything and wait until it is done.

> When it is done, restart your computer

> When rebooted, if not already done, right click the internet connection aren and click enable wireless

> Then left-click it and this might be what you looking for, you'll know it is if you see a list on wireless connections in your area.

---

### Post by Thunder X on 2010-04-08
i am now wondering if my issue has anything to do with the fact i used wubi to install ubuntu? there is also an option to choose ubuntu in recovery mode at boot. anything to that? or perhaps i should select something other than GNOME at the log in screen, i.e. failsafeGNOME or exterm? i will give all of your suggestions a try tomorrow (those i have yet to attempt). i thank everyone for their assistance.

---

### Post by steveneddy on 2010-04-08
> **Thunder X said:**
> i am now wondering if my issue has anything to do with the fact **i used wubi to install ubuntu?** 

DOH!

](*,)

Wubi sucks - go to a VM or install another partition and install Ubuntu for real.

---

### Post by Thunder X on 2010-04-08
> **steveneddy said:**
> DOH!

](*,)

Wubi sucks - go to a VM or install another partition and install Ubuntu for real.

i have no idea what a vm is, but i will uninstall the wubi version and install a "real one" from some where else. i assume these are links here to other resources. thank you kindly steveneddy. can't wait to be done with all of this so i can get back to html and java, stuff that's easy and makes sense. lol

---

### Post by egalvan on 2010-04-09
> **Thunder X said:**
> i am now wondering if my issue has anything to do with the fact **i used wubi to install** ubuntu? 

+1 for

DOH!!

](*,)

Yeah, that makes a big difference.
Even though TECHNICALLY there is none.

Wubi is fine for showing that Linux can run on a machine,
but it can cause all sorts of problems...

At this point, Iam wondering if it makes more sense for you to wait for Lucid Lynx 10.04 LTS, which is due 29-April,
a mere two weeks...
(I'm running the Beta 2, and it's been fine for me, knocks on wood)

You can spend that time making back-ups of your data, and getting a good partition editor, such as PartedMagic.

[http://www.partedmagic.com](http://www.partedmagic.com)


As for where to download Ubuntu, here is the main Ubuntu site

[http://www.ubuntu.com/](http://www.ubuntu.com/)

remember that 10.04 is ***BETA*** and as such can be un-stable (crash, freeze, lose data).
I use it, and thousands are using it....
JUST BE AWARE OF THE BETA STATUS RIGHT NOW.
wait two week, and it will "go gold"

---

### Post by egalvan on 2010-04-09
> **durand said:**
> Remember to look at the right post! One was for you, the other for taylo31.

The main reason we ask that folks start their own threads... :confused:

---

### Post by Thunder X on 2010-04-09
> **egalvan said:**
> +1 for

DOH!!

](*,)

Teah, that makes a big difference.
Even though TECHNICALLY there is none.

Wubi is fine for showing that Linux can run on a machine,
but it can cause all sorts of problems...

At this point, Iam wondering if it makes more sense for you to wait for Lucid Lynx 10.04 LTS, which is due 29-April,
a mere two weeks...
(I'm running the Beta 2, and it's been fine for me, knocks on wood)

You can spend that time making back-ups of your data, and getting a good partition editor, such as PartedMagic.

[http://www.partedmagic.com](http://www.partedmagic.com)


well, i've gone and uninstalled it, but i still get the option for ubuntu or windows at the boot screen. i don't know how to get rid of it. this is far more than i bargained for. i thought it was something i could install and be finished with it. i don't like having to type in commands and such. i did that in the 80's, why should i be doing it three decades later? i'm going to find someone here in new york to get rid of it and install it anew. i certainly appreciate everyone here trying to assist me.

---

### Post by geekwanabe on 2010-04-09
Hey ThunderX, if you're still checking this, they are right about the BCM driver.  I had the same problem after a clean install of Karmic without WUBI.  Synaptic Package Manager will fix it.  I did this yesterday.

I'm clueless with computers and I just come here if there is a problem and copy and paste.  You can do this!

---

### Post by steveneddy on 2010-04-10
> **Thunder X said:**
> i have no idea what a vm is.....

A VM is a [Virtual Machine]("http://en.wikipedia.org/wiki/Virtual_machine"). It allows you to install alternate operating systems while running your main OS.

I use [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") and find it very stable and useful. It is free for Windows. DL this to install Ubuntu on your Windows machine and be free of Wubi. 

[Good luck - we're all counting on you]("http://www.youtube.com/watch?v=SmHeP9Sve48").

---

