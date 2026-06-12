---
title: "Absolute Beginner Issues w/ getting Linksys WPC300N wireless card"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by mnemonik on 2008-07-30
Hi everyone! Future thanks for any help!

My stuff:

*Dell Inspiron 6000 laptop w/ ubuntu 8.04

*Linksys WPC300N wireless card

My issues:

I cannot figure out how to get Ubuntu to recognize my wireless card, or get me on the internet. From what I have been able to gather I need to install ndiswrapper (I have so far failed) and it will compile the drivers...? I have the driver for windows and my understanding is that I need inf files?

Please keep in mind I AM AN ABSOLUTE NEW BEGINNER @ UBUNTU/LINUX! I only just figured out where to type these commands like sudo this or that! Please don't hate I'm trying to learn, but very not used to typing commands that I don't understand. STEP BY STEP, SIMPLE HELP IS MUCH APPRECIATED!!!

---

### Post by mordak13 on 2008-07-30
I know this may not help at this exact moment but after reading this article: [http://practical-tech.com/network/atheros-becomes-linux-friendlier/]("http://practical-tech.com/network/atheros-becomes-linux-friendlier/") There's hope just around the corner. Check Linksys's site and possibly Atheros' if they have one offering drivers of any kind. Google is your friend. If the article is true then I'm sure those drivers will be included in Ubuntu post hast.

---

### Post by mnemonik on 2008-07-30
> **mordak13 said:**
> I know this may not help at this exact moment but after reading this article: [http://practical-tech.com/network/atheros-becomes-linux-friendlier/]("http://practical-tech.com/network/atheros-becomes-linux-friendlier/") There's hope just around the corner. Check Linksys's site and possibly Atheros' if they have one offering drivers of any kind. Google is your friend. If the article is true then I'm sure those drivers will be included in Ubuntu post hast.

Wait, why check atheros website if they are a different wireless device manufacturer...? I'll check linksys now, and atheros b/c you suggest it, but it doesn't make sense to me.

---

### Post by mordak13 on 2008-07-30
> **mnemonik said:**
> Wait, why check atheros website if they are a different wireless device manufacturer...? I'll check linksys now, and atheros b/c you suggest it, but it doesn't make sense to me.

It was merely a quick off the top of my head answer. Just trying to offer some suggestions. :cool:

---

### Post by mnemonik on 2008-07-30
ok well, i have been trying to install ndiswrapper and I'm stuck almost as soon as i start. i follow these directions, and i get stuck at prerequisties:

Prerequisites 
=============

You need a recent kernel, at least 2.6.16, with header files for the
kernel. Make sure there is a link to the kernel source from the modules
directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory.



And then this is what I get in the terminal:

mnemonik@mnemonik-laptop:~$ ls /lib/modules/`uname -r`/build
arch    Documentation  include  Kbuild  Makefile        net      security
block   drivers        init     kernel  mm              samples  sound
crypto  fs             ipc      lib     Module.symvers  scripts  usr
mnemonik@mnemonik-laptop:~$ tar zxvf ndiswrapper-version.tar.gz
tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mnemonik@mnemonik-laptop:~$ 




I'm missing the .config from the first command's results, i thought screw it lets try the next thing anyways and i got an error that i have no idea what it means besides something is missing...

---

### Post by mnemonik on 2008-07-31
mnemonik@mnemonik-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:14:22:e7:e0:e8
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
*-network:1
description: Wireless interface
product: PRO/Wireless 2915ABG Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:03:03.0
logical name: eth1
version: 05
serial: 00:13:ce:c5:0b:4a
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
*-network UNCLAIMED
description: Network controller
product: BCM43XG
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 32 bits
clock: 33MHz
configuration: latency=0
mnemonik@mnemonik-laptop:~$

From what I can tell, Ubuntu is picking up my ethernet and built in wireless (which hasn't worked for a while, common problem with dell laptops) but it is not recognizing the linksys wireless card. Am I right?

---

### Post by mnemonik on 2008-07-31
I managed to install ndiswrapper, its utilities, and ndisGTK, by following this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But i get stuck at this part here: 
#

Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key.
#

Look through the output of the lspci command for an entry for your wireless card.
#

Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0.
#

Now, type lspci -n into the Terminal and press return.
#

Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400. 

I can't find my wireless card using lspci or lsusb...

---

