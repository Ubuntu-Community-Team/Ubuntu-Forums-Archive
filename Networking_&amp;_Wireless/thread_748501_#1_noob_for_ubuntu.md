---
title: "#1 noob for ubuntu"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by MC21 on 2008-04-07
My 7.10 disk came today and i've installed it onto my PC which has a Linksys WMP11 PCI card.


I've heard something about NDISwrapper, but really... I haven't got a clue :confused:

---

### Post by fitzbuntu on 2008-04-07
Hi I remember my early wireless difficulties.

ndiswrapper is a utility that allows you to use Windows drivers in a Linux environment. First off go to this page for info on how to install ndiswrapper:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Or just use synaptic and search for **ndiswrapper**. Whilst you're at it you could try downloading **ndisgtk** which is a GUI front-end.

If you use ndisgtk you can simply upload the drivers for your card from the desktop, if that doesn't work then open a terminal and follow the instructions here (after installing ndiswrapper):

Install a driver:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-b30aaebf79b1393631b352f8f7a1acf5b17da38c)

If network manager doesn't pick up an access point this will show you how to get going using the command line.

Setup Unencrypted/WEP:
[http://ubuntuforums.org/showthread.php?t=571188&highlight=8180](http://ubuntuforums.org/showthread.php?t=571188&highlight=8180)

Setup WPA:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=rt61](http://ubuntuforums.org/showthread.php?t=202834&highlight=rt61)

---

### Post by ugm6hr on 2008-04-07
To get advice on wifi - post the output from the following command (capital C) - see the link in my signature to find out where to enter the Code:
```
lshw -C network
```

And let us know the following:
1. Do you "hide" your SSID? (If you don't know what that means - the answer is probably no)
2. What encryption do you use? i.e. WEP/ WPA
3. Do you use MAC filtering?  (If you don't know what that means - the answer is probably no)
4. Can you get online with a wired connection?
5. Which version of Ubuntu? i.e. 7.10, 64-bit etc.

---

### Post by MC21 on 2008-04-07
Ok thanks for your help, it says the driver is installed but the hardware is not found. =/

EDIT:
1. Do you "hide" your SSID? (If you don't know what that means - the answer is probably no) - **nope**
2. What encryption do you use? i.e. WEP/ WPA **it's not encrypted**
3. Do you use MAC filtering? (If you don't know what that means - the answer is probably no) **nope**
4. Can you get online with a wired connection? **haven't tried, and I can't access it really. PC upstairs router downstairs**
5. Which version of Ubuntu? i.e. 7.10, 64-bit etc. **7.10**

---

### Post by ugm6hr on 2008-04-07
> **MC21 said:**
> Ok thanks for your help, it says the driver is installed but the hardware is not found. =/

You will need to copy and paste the entire output here.  At least the bit I've highlighted for scraghty.

If you can't get online at all (with wired) - this can be done by copying to a text file on a USB stick.

The full result from lshw would be useful (if possible), rather than just the 2 lines.

Be aware, that if you can't get online with wired, the solution will probably require a lot of transferring files with USB.

---

### Post by ugm6hr on 2008-04-07
I've realised that a second user had comandeered this thread - so I've separated the 2 problems.

Other user here: [http://ubuntuforums.org/showthread.php?t=748633](http://ubuntuforums.org/showthread.php?t=748633)

---

### Post by MC21 on 2008-04-08
james@james-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth1
       version: 02
       serial: 00:06:25:23:27:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b

That's what it says when I type lshw -C network

---

### Post by ugm6hr on 2008-04-08
As I suspected, you have a notorious Broadcom  wifi card (BCM4303).

There are 2 options for wifi - the pros and cons are heavily documented elsewhere.

1. bcm43xx driver with fw-cutter
2. ndiswrapper

BCM43xx

If you cannot get online from the Ubuntu computer, see here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-60c0dd48972d93f123f836302cc92fc54ba66408](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-60c0dd48972d93f123f836302cc92fc54ba66408)
This confirms your card is supported: [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

ndiswrapper

There are plenty of threads on how this is done.

Simplest method is to download and install (double-click):
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk)

Then use the .inf and .sys from your Windows installation (something like bcmwl5.inf and bcmwl5.sys - put them in the same directory) - select the .inf file from "Windows Wireless Driver" from the menu.

There are a few more steps to this - detailed here: [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

