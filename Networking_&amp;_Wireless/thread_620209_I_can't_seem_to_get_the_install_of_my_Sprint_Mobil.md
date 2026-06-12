---
title: "I can't seem to get the install of my Sprint Mobile Broadband via Novatel U727"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by thecomputerdoc on 2007-11-22
I can't seem to get the install of my Sprint Mobile Broadband via Novatel U727. Can you tell me how you did it. I can't get it. Someone had posted that they pulled 1833 kb/s over USB1.1.
I've tried a few things but nothing seems to work. I've tried GOMONE ppp and it doesn't recognize my modem. I've tried all of the available settings, and nothing. I have installed it on a desktop running WINXP Pro and that works perfectly. I just dont understand it. HELP

---

### Post by vrod74 on 2007-11-22
go to sprint.com and download the .pdf document they have for linux. 


link: [http://sprint.com/downloads](http://sprint.com/downloads)

Choose Linux as the OS and download the .pdf document...  I have u720 and I have it running under Ubuntu 7.10.

---

### Post by technoshaun on 2007-11-25
I followed the directions in that PDF file and I still can't get it working in Kubuntu 7.10 is there something else I need to download for Gutsy?

--Shaun

---

### Post by technoshaun on 2007-11-27
Found what I was missing down at the very bottom of the PDF file here is what you have to do to use the device in (K)Ubuntu --

Insert U727 After Logging in to Gnome or KDE

Open a terminal and use the following commands:

sudo modprobe –r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100”
sudo eject /scd1
sudo dmesg|grep –i ttyUSB (not necessary but makes sure the driver loaded correctly)

Start surfing the web.

---

### Post by thecomputerdoc on 2007-11-27
Technosaun,
Can you tell me what the command sudo eject /scd1 means. It won't work on my system.
Thanks,
The Computer Doctor

---

### Post by RandyNose on 2007-12-09
> **vrod74 said:**
> go to sprint.com and download the .pdf document they have for linux. 


link: [http://sprint.com/downloads](http://sprint.com/downloads)

Choose Linux as the OS and download the .pdf document...  I have u720 and I have it running under Ubuntu 7.10.

This is the direct link for the Sprint Mobile Broadband Guide.

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)


This package contains a PDF of instructions on how to configure a Linux OS to use a Sprint Mobile Broadband (modem) device to connect to the internet.This PDF is provided for informational purposes only. Supported devices include:

Sierra
AC580
AC595
AC595U
AC597E

Novatel
S620
S720
U720
EX720
U727

Pantech
PX-500

---

### Post by sandwormblues on 2008-02-13
Obviously the sprint guide is the first place i looked.

Unfortunately, the sprint guide is useless.  As far as Linux is concerned, the U727 is a piece of CRAP.  I would recommend to everyone who reads this to use ANY other evdo card, which will undoubtedly be easier to set up and have better throughput.

---

### Post by tech1_contact on 2008-04-04
> **sandwormblues said:**
> Obviously the sprint guide is the first place i looked.

Unfortunately, the sprint guide is useless.  As far as Linux is concerned, the U727 is a piece of CRAP.  I would recommend to everyone who reads this to use ANY other evdo card, which will undoubtedly be easier to set up and have better throughput. 

I have a sprint Pantech PX-500 and i cant get that running.
I have a big problem installing this due to i cant connect to the internet to download the packages.
so i tryed to download the kppp package with windows xp and i draged it to ubuntu but it tell's me dependencies not supported.
I am stuck cause all i have for internet is the sprint network.
have you had any problems like this or can anyone help.
O and i am not to good with ubuntu yet.:confused:
tech1_contact@ yahoo messenger

---

### Post by sandmanfvr on 2008-04-21
I got my U727 running fine, and it is not crap.  Only thing is the kppp limits it to 64KB a second.  I get 2 or sometimes 3 times that in windows.  Any way to fix this?

---

### Post by sandmanfvr on 2008-04-21
Bump once so maybe get some help, it not oh well.

---

### Post by sandmanfvr on 2008-04-21
Ok, one more bump, then I will give up on this.  *sigh*

---

### Post by Almumin on 2008-04-24
I was cleaning up my computer and found this Sprint Mobile Setup go-by PDF. :)Here you go.

Almumin

---

### Post by Almumin on 2008-04-24
wow...just saw your posting. i will see if I can find something. I setup mine up but it wasn't in KDE it was in GNOME.

---

### Post by tdubois65 on 2008-05-20
I used the Sprint documentation to setup my 727 and it is screaming!

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

I'm getting over 1100kbps download.  I'm running Hardy Heron (8.04) and had Verizon Wireless in my Windows days.  I see there are kludgy instructions for rigging the PC5740, but not my PC5750, plus Verizon has zero help for setting up on Linux.  While I'm disappointed that Sprint does not have software for Linux, they at least have easy to follow instructions for getting the card working and it's working using kppp.  

Good-bye Verizon, maybe later

Weening myself from Windows has been quite painful over the past week, but it's worth it.  Biggest loss = iTunes

---

### Post by Almumin on 2008-05-20
Have you ever tried Banshee? [http://www.banshee-project.org/Main_Page](http://www.banshee-project.org/Main_Page) =)

> **tdubois65 said:**
> I used the Sprint documentation to setup my 727 and it is screaming!

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

I'm getting over 1100kbps download.  I'm running Hardy Heron (8.04) and had Verizon Wireless in my Windows days.  I see there are kludgy instructions for rigging the PC5740, but not my PC5750, plus Verizon has zero help for setting up on Linux.  While I'm disappointed that Sprint does not have software for Linux, they at least have easy to follow instructions for getting the card working and it's working using kppp.  

Good-bye Verizon, maybe later

Weening myself from Windows has been quite painful over the past week, but it's worth it.  Biggest loss = iTunes

---

