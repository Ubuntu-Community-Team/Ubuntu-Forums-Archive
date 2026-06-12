---
title: "Trying to get drivers to allow me to install D-link DWA-171 wireless usb adapter."
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by moyer137 on 2014-10-27
I'm new to Linux.

I have a dual partition on my computer:Windows Vista (which runs fine, I've already installed the wireless software and it works well) and Ubuntu 14.04. The Ubuntu log in screen loads normally, but after I log in the screen goes black after about three seconds. I suspect my video card needs updated. I can bring up the terminal from the black screen, but I can't update my drivers with sudo apt-get update (I'm guessing because I'm not connected to the internet). I've also thought maybe getting gnome would allow me to view the screen (I had fedora 16 for a short time and was able to see that, I believe it used gnome), but I don't know how to go about that either.

I found a thread that apparently solves my problem here [http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426), but I don't know how to read it. I went to the address they suggest downloading the drivers from ([http://wikidevi.com/wiki/D-Link_DWA-180_rev_A1](http://wikidevi.com/wiki/D-Link_DWA-180_rev_A1)) and downloaded from the 'available on Edimax's site' under 'Probable Linux driver' section on the sidebar to the right of the screen onto a usb device. I don't understand the files or what to do with them when I open them up to look at them (some of them automatically try running things). I also don't know what a 'make' command is. 

So I need know if it is possible for me to run the necessary files from the usb stick in the terminal and then be able to get wifi and then get my screen powered on. Any help would be greatly appreciated!):P

---

### Post by JeQhdMD on 2014-10-28
It seems the issue with video needs fixing first . . . to do that, we will need the specs for your system (especially the gpu info e.g., nvidia??,. ati ??, intel  . . )  Suspect screen is going black because Ubuntu's default desktop is using Unity which requires 3d acceleration (meaning the appropriate video drivers need download and install (from within Ubuntu . . not 3rd party site).  

A couple "simpler" ways to do dual boot on your system would be to:
1.   Install Xubuntu 14.04 with xfce desktop (and just like that, you'll have full video support),
2.   I wouldn't mess with the D-link dwa-171 as the support for it is limited to an older kernel than comes with any buntu 14.04.   There is a way around that, but it's not newby friendly at all (to do and then to maintain).   So, get an alternative usb wireless adapter that works out of the box:
>>>   Panda Ultra wifi a/g/n OR TP Link 722n OR Airlink 101  . . . these generally work without the need to install drivers (I prefer the TP Link 722 - - really good range.)   All are available via Amazon for 10-25 usd.

By the way . . "make" is not a newby friendly topic.   What it means is you are "compiling" an application . . . in other words, your "building" an app instead of installing a pre-compiled binary program.   The normal and preferred way for linux newcomers is to install apps (packages) is using the provided package manager (Ubuntu Software Center) or the legacy package manager "Synaptic".   Just click the install button and you're done!   Linux has about a dozen different methods to install apps, but Ubuntu Software Center is easiest.

Just my two cents so you don't beat your head against the wall and get discouraged.   As you gain experience, you can always learn the intermediate admin steps of compiling, creating scripts, learning & using detailed bash commands, etc (if you're so inclined).

---

### Post by Bucky Ball on 2014-10-28
Welcome. Please post separate threads for separate support issues (i.e. edit out the video support request and post it in another appropriately titled  thread). Makes it less confusing and that's how it's done around these parts. ;)

I am going to address what is addressed in the title of the thread. Are you sure you need drivers? Please open a terminal and, with the USB plugged in, paste these two commands in one at a time, hitting return after each:

 ```
sudo lshw -C network
lsusb 
```

Post the two outputs back here in [code] tags (see the last link in my signature to see how).

DON'T install ndiswrapper if you come across any pages advising that course. Last resort and rarely needed now.

(But yes, you should try and fix the video problem first. Post another thread and the link to it back here, please. Good luck.)

---

### Post by moyer137 on 2014-10-28
Ok, sorry for the confusion! I'm now running Xubuntu 14.04.1 (thanks JeQhdMD!) and it looks great. I typed in sudo lshw -C network and got:

```
 *-network:0
                  description: Ethernet interface
                  product: RTL-8100/8101L/8319 PCI Fast Eathernet Adapter
                  vendor: Realtek Semiconductor Co., Ltd.
                  physical id: 4
                  bus info:pci@0000:01:04.0
                  logical name: eth1
                  version: 10
                  serial:00:1d:0f:c3:83:21
                  size: 10Mbit/s
                  capacity:100Mbit/s
                  width: 32 bits
                  clock: 33MHz
                  capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                  configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                  resources: irq:16 ioport:cc00(size=256) memory:fdefe000-fdefe0ff memory:fdec0000-fdedffff
       *-network:1
                  description: Ethernet interface
                  product:NM10/ICH7 Family LAN Controller
                  vendor: Intel Corporation
                  physical id: 8
                  bus info: pci@0000:01:08.0
                  logical name: eth0
                  version: 01
                  serial: 00:1a:92:5b:fe:4e
                  size: 10Mbit/s
                  capacity: 100Mbit/s
                  width: 32 bits
                  clock: 33MHz
                  capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                  configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                  resources: irq:20 memory:fdefd000-fdefdfff ioport:c800(size=64)

```

This might sound silly, but I typed that all out. Is there an easy way for me to copy and paste the lsusb information? I have an dentist appointment I have to run to right now, but I'll post the lsusb when I get back. Thanks for the help so far!

---

### Post by Penguin360 on 2014-10-28
First of all, I think this post needs to be moved to Installation and Upgrades.

Back to your topic. I would suggest you to connect your computer to your router with a cable so you can have Internet connection, then go to System Settings > Software& Updates > "Additional Drivers" tab, then do a scan for proprietary drivers for your video card and Ethernet adapter, then install the correct proprietary drivers to make the wireless adapter work. This is how I got my video card issue solved ([http://ubuntuforums.org/showthread.php?t=2249788](http://ubuntuforums.org/showthread.php?t=2249788))

---

### Post by moyer137 on 2014-10-28
my lsusb reads:

```

Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 003: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 002: ID 2001:3314 D-Link Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by JeQhdMD on 2014-10-28
Since the install completed fine (using Xubuntu 14.04) - - that part of the thread (video display) is done.  I've read through several "long" threads about issues with this adapter - did not see any reliable or persistent fixes - - even with kernel updates.     Repeat suggestion for "moyer137" to use a more compatible wireless adapter product . . 

Atheros drivers are usually a good match (as several were open-sourced years ago).
 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
|| Brand || Model || Chipset || Driver || Plug and Play || Phone ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 TP-Link || TL-WN722N || AR9271  || ath9k_htc || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 TP-Link || TL-WN822N || AR7010 || ath9k_htc || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """"" || """"" || AR9287 || """"" || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  Airlink || AWL5088 || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """" || """" || RTL8192CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 Panda || Ultra Wifi || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 """" || """" || RTL8192CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 Edimax || EW-7811UN || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ASUS || USBN13 || RTL8188CUS || ??? || Yes ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ||  ||  ||  ||  ||  ||
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by Bucky Ball on 2014-10-28
*Thread moved to **Networking & Wireless**.*

> **Penguin360 said:**
> First of all, I think this post needs to be moved to Installation and Upgrades.



Thanks for sharing, but be aware that ***Installations & Upgrades*** is:

> For questions about upgrading and installation of your new **Ubuntu OS**.

... and not about installing and upgrading drivers or apps. If you have any thoughts you'd like to relate to staff in the future simply use the 'Report Thread' button and we'll get back to you.

---

