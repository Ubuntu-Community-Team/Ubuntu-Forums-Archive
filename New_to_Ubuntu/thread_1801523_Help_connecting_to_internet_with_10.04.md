---
title: "Help connecting to internet with 10.04"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by genwin on 2011-07-10
Hi guys. First time Ubuntu user here (first linux install ever). I have it on dual boot
with Vista. From what I have been reading, Ubuntu for the most part does not require 
driver installations like Windows does (correct me if I am wrong). I have a Prolink H9200 ADSL2+ Modem/Router. It works fine on Vista, can't seem to get it to work on Ubuntu. Upon further reading, I encountered lsusb so here it is:

```

jeff@jeff-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0915:0005 GlobeSpan, Inc. LAN Modem
Bus 004 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeff@jeff-desktop:~$ 

```Hope this helps. Thanks.

---

### Post by wep940 on 2011-07-10
If you have a user name and password for the DSL, you may need to use PPPOE to do so:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by genwin on 2011-07-10
> **wep940 said:**
> If you have a user name and password for the DSL, you may need to use PPPOE to do so:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)


Upon reading, I saw this:

If you are connecting to the modem with a usb cable, this guide is not for you.

---

### Post by wep940 on 2011-07-10
Crap.

I've done a search on the net using the name and the USB id's (xxxx/xxxx) and linux to see what needs to be done.  Still sorting through all kinds of things.  you may want to look yourself as well.

---

### Post by wep940 on 2011-07-10
I've seen reference to the following, but with warnings it is outdated.  Be aware that other users in other Linux systems have reported problems as well and no solution has been found.

download this file:

eciadsl-synch_bin.tar.bz2

from:

[http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)

You'll need to unpack the file and then search for a readme.

---

### Post by genwin on 2011-07-10
> **wep940 said:**
> Crap.

I've done a search on the net using the name and the USB id's (xxxx/xxxx) and linux to see what needs to be done.  Still sorting through all kinds of things.  you may want to look yourself as well.


I've been looking. But since this is my first encounter with Ubuntu, I don't know exactly what to search for. Hopefully I can get this solved though. It's a pain rebooting to Vista just to look for stuff related to Ubuntu. Many thanks anyway.

---

### Post by bheemamahesh on 2011-07-10
if ur Internet is DSL...This will works fine


**sudo pppoeconf**

A text-based menu program will guide you through the next steps, which are:

Confirm that your Ethernet card is detected.
[I]Enter your username (provided by your ISP).
Enter your password (provided by your ISP).[/I]
If you already have a PPPoE Connection configured, you will be asked if it may be modified.
Popular options: you are asked if you want the 'noauth' and 'defaultroute' options and to remove 'nodetach' - choose "Yes".
Use peer DNS - choose "Yes".
Limited MSS problem - choose "Yes".
When you are asked if you want to connect at start up, you will probably want to say yes. (This option does not work) See the secton "Connecting on Boot"
Finally you are asked if you want to establish the connection immediately.
Once you have finished these steps, your connection should be working.

Manual connection control


_To start your ADSL connection (Internet) on demand, in a terminal type:_

**pon dsl-provider**


_To stop your ADSL connection (Internet), in a terminal type:_

**poff dsl-provider**

---

### Post by wep940 on 2011-07-10
I thought PPPOE was needed, but I guess I pointed the OP to the wrong thread.   The only "trick" is the USB part.  Thanks for clearing that up!

---

### Post by jmore9 on 2011-07-10
If anyone could explain why is it so differnet between the ethernet connection and the usb one.  I use a dsl modem with the ehternet connection had no issues.

Just curious.

---

### Post by jtarin on 2011-07-10
[This page]("http://eciadsl.flashtux.org/download.php") links to a USB driver for your modem and instructions for installing. It is a little dated and this driver might be included in the kernel as of this time. I doubt it though.

> You can try EciAdsl if your modem is not in supported list (neither unsupported list), only if you have **_Globespan chipset._**

Download and install EciAdsl, then run script ecidasl-probe-device.sh.

Note VID/PID found, and search them in our supported modem list (VID1/PID1):
- if you see a modem with same VID1/PID1, then note appropriate VID2/PID2 and chipset (GS7070 or GS7470).
- if you don't see your VID/PID in our list, then try both settings :
    chipset=GS7070, VID1=VID, PID1=PID, VID2=0915, PID2=PID+1
    chipset=GS7470, VID1=VID, PID1=PID, VID2=VID, PID2=PID

After setup, try all possible synch .bin files (according to your chipset) if you have synch or connection problems.

If you manage to connect with your modem, please let us know, we'll add it to the supported modems list.


[Forums for help]("http://eciadsl.flashtux.org/forum/viewforum.php?f=5&sid=71073df5025a99964970a222c4f573f0")

---

### Post by wep940 on 2011-07-11
Isn't this what was in the link I posted in a previous post?
 
And....if the OP doesn't know, when you do a lsusb, you'll see a 4 character string, a colon, and another 4 character string.  The first 4 characters are the USB manufacturer/vendor id, the second is the product id.  You need those in the link.

---

### Post by jtarin on 2011-07-11
> **wep940 said:**
> Isn't this what was in the link I posted in a previous post?
 
And....if the OP doesn't know, when you do a lsusb, you'll see a 4 character string, a colon, and another 4 character string.  The first 4 characters are the USB manufacturer/vendor id, the second is the product id.  You need those in the link.Yea but mine was to a Ubuntu/Debian .deb file.:P

---

### Post by genwin on 2011-07-11
> **bheemamahesh said:**
> if ur Internet is DSL...This will works fine


**sudo pppoeconf**

A text-based menu program will guide you through the next steps, which are:

Confirm that your Ethernet card is detected.
[I]Enter your username (provided by your ISP).
Enter your password (provided by your ISP).[/I]
If you already have a PPPoE Connection configured, you will be asked if it may be modified.
Popular options: you are asked if you want the 'noauth' and 'defaultroute' options and to remove 'nodetach' - choose "Yes".
Use peer DNS - choose "Yes".
Limited MSS problem - choose "Yes".
When you are asked if you want to connect at start up, you will probably want to say yes. (This option does not work) See the secton "Connecting on Boot"
Finally you are asked if you want to establish the connection immediately.
Once you have finished these steps, your connection should be working.

Manual connection control


_To start your ADSL connection (Internet) on demand, in a terminal type:_

**pon dsl-provider**


_To stop your ADSL connection (Internet), in a terminal type:_

**poff dsl-provider**

Hi. I don't have an ethernet card. Thanks.

---

### Post by genwin on 2011-07-11
> **jtarin said:**
> [This page]("http://eciadsl.flashtux.org/download.php") links to a USB driver for your modem and instructions for installing. It is a little dated and this driver might be included in the kernel as of this time. I doubt it though.



[Forums for help]("http://eciadsl.flashtux.org/forum/viewforum.php?f=5&sid=71073df5025a99964970a222c4f573f0")


I will "try" this in a moment. I am new to Ubuntu and this looks complicated. And why is it on Windows, I just have to install the driver from the CD and the modem works? Can't the same thing be done with Ubuntu?

---

### Post by wep940 on 2011-07-11
Manufacturers know that if they want to sell their product, it needs to work with Windows.  For the home market PC it is by far the prevalent OS.  Linux is free, and we want things to be open source (so we can see and modify the source for, in this case, a driver, if we want to).  The vendors don't normally want to spend time/money on developing a Linux driver.  So, there are some vendors that are very Linux friendly, there are others not so much, and more who don't do anything.

So, in your case, there doesn't appear to be a native Linux driver from the vendor.  The package we have pointed you to is the driver which in your case just requires a little more work.

Please do the download, unpack the file, then look at the readme's, etc., to see what is required to get this working.  If you have questions, just post back.  Just because we don't have your adapters' chipset doesn't mean we still can't try to help.  I've gone so far as to download things like you need and see what I have to do to build it even though I have no use for it, just to help someone if possible.

Also, someone correct me if I'm wrong, but I don't believe we can use ndiswrapper and the Windows drivers in this case since a modem device, not a network interface device.

---

### Post by jtarin on 2011-07-11
> **genwin said:**
>  And why is it on Windows, I just have to install the driver from the CD and the modem works?Because the manufacturer of this modem has not supplied a Linux driver, so one had to be made for it. Would it be any differnt if it were on a CD? Not much.[/QUOTE]

> **genwin said:**
>  Can't the same thing be done with Ubuntu?Yes it could if the manufacturer would support Linux. More manufacturers are supporting Linux everyday. The modem you have is not the newest and Linux developers must constantly make new drivers for newer hardware and it is a difficult job that no one pays them to do and they do it in their own time. The file I linked you to is a .deb file which installs as easily as something on windows.

---

### Post by genwin on 2011-07-11
Thanks wep940 and jtarin. I will try that and post the results later. Actually, the modem as mentioned is old. I've been using the same one for 5 years and thinking of buying a new one as it's disconnecting so often. Any suggestions on what to buy (so it works fine with ubuntu)?

And also with GRUB, I have these options along side Vista:

Ubuntu ... 2.6.32-21-generic
Ubuntu ... 2.6.32-21-generic (recovery mode)
Ubuntu ... 2.6.32-22-generic
Ubuntu ... 2.6.32-22-generic (recovery mode)

Is there a major difference between those? Thanks.

---

### Post by jtarin on 2011-07-11
> **wep940 said:**
> Manufacturers know that if they want to sell their product, it needs to work with Windows.  For the home market PC it is by far the prevalent OS.  Linux is free, and we want things to be open source (so we can see and modify the source for, in this case, a driver, if we want to).  The vendors don't normally want to spend time/money on developing a Linux driver.  So, there are some vendors that are very Linux friendly, there are others not so much, and more who don't do anything.

So, in your case, there doesn't appear to be a native Linux driver from the vendor.  The package we have pointed you to is the driver which in your case just requires a little more work.

Please do the download, unpack the file, then look at the readme's, etc., to see what is required to get this working.  If you have questions, just post back.  Just because we don't have your adapters' chipset doesn't mean we still can't try to help.  I've gone so far as to download things like you need and see what I have to do to build it even though I have no use for it, just to help someone if possible.

Also, someone correct me if I'm wrong, but I don't believe we can use ndiswrapper and the Windows drivers in this case since a modem device, not a network interface device.There's a link to an Ubuntu .deb file on that page so it shouldn't be difficult.

---

