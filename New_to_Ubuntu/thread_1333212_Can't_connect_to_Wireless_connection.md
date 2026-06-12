---
title: "Can't connect to Wireless connection"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by PDA1 on 2009-11-21
I can't get Ubuntu to connect to my wireless router in my house when using my notebook.

It will connect via ethernet cable with no problem.

But, I can't connect using my notebooks wireless connection.  (in Windows it works perfectly)

How do I do it?

I'm using Ubuntu 9.10  on a dual boot drive.

---

### Post by frenchn00b on 2009-11-21
ifconfig ?

iwlist scan ?

---

### Post by bilbo.san on 2009-11-21
When connected using the Ethernet wired, try to set the wireless to work as well... that might bring a notice that some 'updates' may be needed in order to work (that happened to me), or you could run a full system update for all recommended and important updates. That might help.

---

### Post by PDA1 on 2009-11-21
I'm really new to this stuff so I have no idea what you're asking me and how to do it.

---

### Post by miguel_d on 2009-11-21
> **PDA1 said:**
> I'm really new to this stuff so I have no idea what you're asking me and how to do it.

go to system -> administration -> update manager, then click install updates

---

### Post by nadian on 2009-11-21
you might find some help if you read through posts at
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by RedSingularity on 2009-11-22
Open a terminal in the accessories area.  The type "lspci" in the terminal and post the output here.

---

### Post by PDA1 on 2009-11-23
I hope this helps.


Reading package lists... Done
owner@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by EnGorDiaz on 2009-11-23
> **PDA1 said:**
> I hope this helps.


Reading package lists... Done
owner@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

simply connect through ethernet then goto restricted drivers in system menu i think its in preferences

---

### Post by PDA1 on 2009-11-23
It's the System>Administration> hardware drivers.

It then mentions 2 wireless drivers.

I click on 1 of them to get it (or whatever it supposed to do)

It looks to authenticate.

I click authenticate.

AUTHENTICATE just sits there doing nothing.

But...when I get frustrated enough I click CANCEL

MIracle of miracles....some downloading of a driver occurs but then it says "This driver isn't activated".   

I click ACTIVATE and it does nothing.  No action at all.

On wonder what's up?

---

### Post by ukripper on 2009-11-23
you need bcmwl-kernel-source for this chipset. 

You can follow this link - [http://blog.alvonsi.us/2009/10/30/broadcom-bcm4311-on-karmic-koala/](http://blog.alvonsi.us/2009/10/30/broadcom-bcm4311-on-karmic-koala/)

---

### Post by PDA1 on 2009-11-23
What the heck is this guy talking about?  Can you give me an English translation of what he's talking about?  This is so darn frustrating!



After searching in the net about the same cases, I found one package that controls the device (or may be ‘controls’ is not the correct word, but let out it that way to make it easier). It is called ***bcmwl-kernel-source***. So I try to search it on the USB Startup Disk (or Live CD), since I am sure that it must be in there to make the device run on Live USB mode. And yes,  I found it with it’s two dependencies, ***dkms*** and ***patch***. Find them in these folders of your Live USB:
 
[LIST=1]
[*]/pool/main/p/patch/patch_2.5.9-5_i386.deb
[*]/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb
[*]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
[/LIST]
 Install them according to the sequence I gave you, and reboot your Karmic. How to install them? Well … just double click on the files and it will guide you to the rest of the process ^^

---

### Post by ukripper on 2009-11-23
> **PDA1 said:**
> What the heck is this guy talking about?  Can you give me an English translation of what he's talking about?  This is so darn frustrating!



After searching in the net about the same cases, I found one package that controls the device (or may be &#8216;controls&#8217; is not the correct word, but let out it that way to make it easier). It is called ***bcmwl-kernel-source***. So I try to search it on the USB Startup Disk (or Live CD), since I am sure that it must be in there to make the device run on Live USB mode. And yes,  I found it with it&#8217;s two dependencies, ***dkms*** and ***patch***. Find them in these folders of your Live USB:
 
[LIST=1]
[*]/pool/main/p/patch/patch_2.5.9-5_i386.deb
[*]/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb
[*]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
[/LIST]
 Install them according to the sequence I gave you, and reboot your Karmic. How to install them? Well &#8230; just double click on the files and it will guide you to the rest of the process ^^


Ok here in English:

Put your Live cd in your Cdrom drive. Once it shows up on your Desktop double click on it. it will open up in File manager. You can see so many files and folders there. Click on pool directory then find below packages:
[LIST=1]
[*]/pool/main/p/patch/patch_2.5.9-5_i386.deb
[*]/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb
[*]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
[/LIST]

Double click and install them one by one, starting from "1." and in exact order.

Hope that is clear.

---

### Post by PDA1 on 2009-11-23
FIXED!!!!!!

Believe it or not.....here's what happened.

1.  My Ubuntu system crashed
2.  I downloaded and burned another copy of Ubuntu 9.10 using InfraRed (or whatever the burner is called on the Ubuntu site.

3.  I reinstalled Ubuntu.  During the reinstallation I saw stuff on the setup that I hadn't seen on previous installations-  I suppose that the burner I used before was corrupted.

4.  Updated Ubuntu (I'm tired of typing that word so I'll call it U using ethernet.

5.  Still couldn't connect so I found some help at this link- [http://ubuntuforums.org/showthread.php?t=1334906](http://ubuntuforums.org/showthread.php?t=1334906)

6.  Give the frustration level I was experiencing I just started added stuff to the Terminal window and hoping something would happen.  Well, it did.  This command sudo apt-get install b43-fwcutter fixed the problem.

WHAT A PAIN IN THE NECK!!!  I've spent at least 15 hours on this problem!!!!!

Thank you for all of your help.  Your patience is like Job's.

---

