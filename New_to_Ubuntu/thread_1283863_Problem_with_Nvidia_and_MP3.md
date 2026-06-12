---
title: "Problem with Nvidia and MP3"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by sgd1977 on 2009-10-06
Hello,

I'm new to Ubuntu (and in general Linux) desktops though I've worked in Unix for a number of years programming/debugging Java and C++.

I would like to evaluate if I can replace my Windows desktop with Ubuntu which has been my primary desktop. The reasons for this are:
1) Windows has gotten too big over the years without order of magnitude more increase in functionality in the base OS (150 MB in Windows 95 to 5GB+ in Windows Vista).
2) I don't play games as much anymore neither do I program in .NET environment so there's nothing to keep me tied to Windows.
3) A lot of my activity has moved online so it doesn't matter which base OS I'm using as long as the browser is competent enough. Both defaults for Windows and Ubuntu (IE8 and FF resp.) satisfy this.
4) It's free :-)

I downloaded and installed Ubuntu 9.04 from the CD on my Acer 4530 notebook. I was impressed that it was able to load drivers for the Wireless card (Atheros) and audio. I was able to browse the web immediately, faster than on a Windows setup.

Now for the problems:
1) My display card is Nvidia GeForce 9100M and some sort of default driver was installed with it. The driver was too slow. Dragging windows was reduced to a slideshow. I was not able to figure out what was the default driver installed and how I can change it. The GUI app for hardware in Ubuntu is far from competent. It only asks me if I want to change my wireless card to the "alternate" driver. There's no way I can check what are the drivers installed for the various hardware components, leave alone how to install it. Browsing the web, I found several people complained about the same problem. I eventually downloaded the "proprietary" driver from Nvidia. Even though it complained that it was for a different Kernel build I installed it anyway as I didn't have any other choice. After this, the desktop became much more responsive and fonts smoothened quite a bit. However, some Ubuntu config windows complained I didn't have the right driver. After a restart, the desktop effects no longer work but the screen is still responsive indicating the proprietary drivers are still being (atleast partly) used.
As a separate point, I don't really understand the philosophy of open drivers - "free as in freedom". If you're using Nvidia you already have proprietary hardware. What are you gaining by using generic drivers that are anyway too slow to be usable?

2) I tried to play MP3 because I wanted to test the sound beyond the Ubuntu chime that is played at startup. Surpisingly, nothing installed by default can play MP3. It is quite daft on Ubuntu's part that an OS released in 2009 doesn't have built-in support for MP3. The "scanning for codecs" by the player couldn't find a codec for MPEG Layer 3 audio. Again very surprising. If this has something to do with licensing, it should say so at install time about installing other codecs, or atleast download them on-demand. Neither of them work. Again, I haven't done any customisation so any optional packages should be downloading from their default location.
How do I get past this? Should I download Winamp?

Can you help me how I am to overcome these problems? If required, I could reinstall the OS.

---

### Post by earthpigg on 2009-10-06
problem 2:

this will solve that problem on a technical level:

```
sudo apt-get install ubuntu-restricted-extras
```

or search for it in any of the two included graphical package managers.

> It is quite daft on Ubuntu's part that an OS released in 2009 doesn't have built-in support for MP3.... If this has something to do with licensing, it should say so at install time about installing other codecs, or atleast download them on-demand. 

sir, i would suggest that any daftness in this regard is not on the part of Ubuntu.

daftness to follow:
[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)
[http://en.wikipedia.org/wiki/Software_patent](http://en.wikipedia.org/wiki/Software_patent)


also see:
[http://en.wikipedia.org/wiki/Free_software#Definition](http://en.wikipedia.org/wiki/Free_software#Definition)
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

if you wish to play MP3s and DVDs the Windows way (instead of ubuntu-restricted-extras, which provides the exact same functionality):
[http://shop.canonical.com/index.php?cPath=19](http://shop.canonical.com/index.php?cPath=19) (look at the Fluendo stuff)

Ubuntu is comprised of [Free Software]("http://en.wikipedia.org/wiki/Free_software"), not [freeware]("http://en.wikipedia.org/wiki/Freeware").

---

### Post by sanguinoso on 2009-10-06
Ubuntu can't install proprietary software due to legal restrictions I believe.

---

### Post by earthpigg on 2009-10-06
for future hardware purchases, it is often a good idea to consult this database first:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

but your video card isn't listed there... thus making your video card potentially a tricky one.

this package claims to provide support for your video card:
[http://packages.ubuntu.com/jaunty/nvidia-glx-173](http://packages.ubuntu.com/jaunty/nvidia-glx-173)

what driver are you currently using? should be in system -> admin -> hardware drivers.... but may not be, since your's appears to be a tricky one.

---

### Post by earthpigg on 2009-10-06
also FYI: "hardware drivers" usually only have one or two drivers listed because for Linux, it's done at kernel level (or close to it)....

the kernel starts up, detects the hardware, and loads the appropriate stuff needed to support that hardware.

this doesn't work, however, with devices wherein manufacturers hide detailed hardware specifications... such as video cards and some/many wireless cards, where reverse-engineering can only do so much :D

that is where ubuntu's jockey-gtk package comes in... (jockey-gtk = system -> admin -> hardware drivers. you can verify this for yourself by right clicking on the top menu -> edit menus -> navigating to the desired item -> 'properties' to see what command the menu actually executes)

---

### Post by lavinog on 2009-10-06
> **sgd1977 said:**
> 
As a separate point, I don't really understand the philosophy of open drivers - "free as in freedom". If you're using Nvidia you already have proprietary hardware. What are you gaining by using generic drivers that are anyway too slow to be usable?


Many times the proprietary hardware requires proprietary drivers that very often contain bugs that can only be addressed by a small group of developers, or are slow to adopt current standards.
open source drivers are free to adopt standards, and bugs can be addressed by anyone.

Here is a recent comparison between ATI's proprietary driver and the open source driver: [http://www.phoronix.com/vr.php?view=14223](http://www.phoronix.com/vr.php?view=14223)
> From the three different test profiles we used and the two graphics cards that were tested, nearly every time the open-source driver stack wound up being faster than the Catalyst 9.10 driver.

What isn't mentioned is that the open source drivers also improve boot times, and contain less bloat.

---

### Post by 3rdalbum on 2009-10-06
It's illegal to distribute Linux with the Nvidia drivers pre-linked, that's why they are not preinstalled. Also, Ubuntu is dedicated to Free and Open-Source Software. There are several technical and philosophical reasons why you might want to use the open-source driver over the proprietary one.

The Hardware Drivers program does not aim to inform you what pieces of hardware you have in your computer and what driver is currently being used for each piece; you really don't need to know. Its aim is to help you install drivers where you have a choice of drivers, and it only works if it knows your specific hardware (the 9100M might be too new for Ubuntu 9.04 to know about; I had only heard of the 9300M and 9400M before now).

Usually Ubuntu will download MP3 codecs on-demand. It doesn't come with them preinstalled because they are not available under a patent-free license, and Ubuntu will not ship any software that uses non-Free patents. I don't know why it's not finding the MP3 codec, but I suspect it might be a case of "you need to go into Synaptic and click Reload to reload the package list".

Alternatively, install the ubuntu-restricted-extras package and enable the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) to get everything sorted out.

---

### Post by sgd1977 on 2009-10-06
> **earthpigg said:**
> problem 2:

this will solve that problem on a technical level:

```
sudo apt-get install ubuntu-restricted-extras
```or search for it in any of the two included graphical package managers.



sir, i would suggest that any daftness in this regard is not on the part of Ubuntu.

daftness to follow:
[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)
[http://en.wikipedia.org/wiki/Software_patent](http://en.wikipedia.org/wiki/Software_patent)


also see:
[http://en.wikipedia.org/wiki/Free_software#Definition](http://en.wikipedia.org/wiki/Free_software#Definition)
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

if you wish to play MP3s and DVDs the Windows way (instead of ubuntu-restricted-extras, which provides the exact same functionality):
[http://shop.canonical.com/index.php?cPath=19](http://shop.canonical.com/index.php?cPath=19) (look at the Fluendo stuff)

Ubuntu is comprised of [Free Software]("http://en.wikipedia.org/wiki/Free_software"), not [freeware]("http://en.wikipedia.org/wiki/Freeware").

Thank you for your reply. I tried the command you gave, this is what I got:
sdesai@Orion:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
sdesai@Orion:~$ 

On the other comments, I'll point you to the following Ubuntu page:
[http://www.ubuntu.com/products/whatisubuntu/904features/music/](http://www.ubuntu.com/products/whatisubuntu/904features/music/)
specifically...

> 
Ubuntu comes with Rhythmbox as the fully-supported music player, one of many choices for playing your music. It is a music player that enables you to plug in your MP3 player, download and share music, access rights-free music stores, share albums across networks and stream live radio.


This is where my expectation was set about out of the box MP3 support.

---

### Post by Sarmacid on 2009-10-06
Try envyng for installing and updating your video card driver.
```
sudo apt-get install envyng-gtk
```

---

### Post by oldos2er on 2009-10-06
"E: Couldn't find package ubuntu-restricted-extras"

 Make sure you have the multiverse repository enabled (System, Administration, Software Sources). Also, you might try updating your sources.list if you haven't done that for awhile.
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lavinog on 2009-10-06
take a moment to read this page:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Click this link to install the restricted extras package: [apt:ubuntu-restricted-extras?section=universe?section=multiverse](apt:ubuntu-restricted-extras?section=universe?section=multiverse)

---

### Post by thiebaude on 2009-10-06
Goto System-Admistration-Hardware Drivers, and let ubuntu search for the drivers, and then choose the recommended driver,I know my nvidia GeForce 8400 gs uses the 180 driver and everything works great.And besides Ubu ntu-restricted-extras I would also do Medibuntu, the w32 codecs that are required to play wmv. videos.And java sudo apt-get install sun-java6.jre sun-java6-plugin

On my ubuntu 9.10 I play all videos and audio.

---

### Post by sgd1977 on 2009-10-09
I did a fresh install of Ubuntu and let the package manager download and install all updates - 200-odd MB and then the hardware driver recommended the nvidia 180 driver. I activated it, while downloading the driver, it said 'jockey backend crashed' or something. Tried again. succeeded this time. the MP3 codecs also downloaded automatically this time. The nvidia driver was propriatary yet was recommended.

---

