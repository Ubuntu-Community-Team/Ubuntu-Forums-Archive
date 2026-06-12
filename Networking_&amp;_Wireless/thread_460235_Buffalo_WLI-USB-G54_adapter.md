---
title: "Buffalo WLI-USB-G54 adapter"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by chaiwalla on 2007-05-31
I am having difficulty installing  this adapter. No luck with Ndiswrapper. In fact I have tried all the various suggestions in the forum.

The device ID is 0411:004b  - by Melco Inc.

Any help/advice would be gratefully received.

---

### Post by tturrisi on 2007-05-31
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by bmartin on 2007-05-31
There are actually two ways to get your wireless working, if it is in fact a Broadcom chipset (it looks like it is).

1. The firmware method: Depending on your chipset, this method can be a little flaky. Here's the [simplest installation method]("http://ubuntuforums.org/showthread.php?t=405990") that I can think of. It's as simple as running one simple script. You can even double-click the script file to perform the installation.

2. The ndiswrapper method: This method generally works flawlessly. Here's a [thread]("http://ubuntuforums.org/showthread.php?t=457371") with two scripts that will get your wireless up-and-running. Both scripts should be run from the command line.

---

### Post by chaiwalla on 2007-06-05
Thanks for that. Both the scripts ran OK but I couldn't seem to get the adapter to work. Pasted below are the various the various  post installation messages.

:~$ ndiswrapper -l

netusg54 : driver installed

        device (0411:004B) present

       ---------------------
:~$ lsusb

Bus 004 Device 004: ID 0411:004b MelCo., Inc. 

Bus 004 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]

Bus 004 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 001 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse

Bus 001 Device 001: ID 0000:0000  

  
 ----------------------------
Network wireless drivers 
Hardware Present: No

---

### Post by bmartin on 2007-06-05
Does the light on the adapter come on? If so, are you using WEP/WPA? If WPA, have you checked the sticky thread related to wireless security in the Networking forum?

Your device seems to be detected.

---

### Post by chaiwalla on 2007-06-05
The device seems to be detected but no light on the adapter.

---

