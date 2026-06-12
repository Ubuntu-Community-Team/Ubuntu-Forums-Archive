---
title: "Inspiron 1501 Wifi Issues"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by kpraytor on 2007-04-25
Ok, I finally got fiesty installed on my vista machine. Now, I am having trouble connecting to a wireless internet connection. When I open up my Network connections, I see an item in the list called "Wireless Connection" and right below that it says "Roaming mode enabled". If I click it and then click proerties, I get a new window that has the "roaming enabled" box checked and all of the other stuff is grayed out. Basically, I need some VERY simple steps as to how to connect to the internet through a wireless connection. Thank you very much for your help!

---

### Post by Buffalo Soldier on 2007-04-25
Firstly we need to know what's your network card and whether Ubuntu has detected it or not. Go to the Terminal/command prompt (Applications -> Accessories -> Terminal) and type in:```
lspci
```and copy-paste here the output. What should you be looking for exactly? Well here's a copy of mine:```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
[COLOR="Blue"][B]01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)[/B][/COLOR]
```
MOST of the time if everything is supported, then you have NO need to go thru network-admin (System -> Administration -> Network). Usually the networking hassle is handle by the network-manager and network-manager applet (nm-applet). Try and look at the top right hand section of your desktop (attaching a screenshot below)

> **kpraytor said:**
> When I open up my Network connections, I see an item in the list called "Wireless Connection" and right below that it says "Roaming mode enabled". If I click it and then click properties, I get a new window that has the "roaming enabled" box checked and all of the other stuff is grayed out.

That's good. Usually it mean your networking is already set to be handled by networking-manager.

---

### Post by kpraytor on 2007-04-25
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev13)
00:14.1 IDE Interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB 600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200m]
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-Tx (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

That sould be it!

---

### Post by kpraytor on 2007-04-25
Ok, the two things that you highlighted in your code I do have in my code, but I do not get the bars in the upper right hand corner. All I get is two computers, one behind another, and there is a small triangle on top of both of them with a "!" in the triangle.

---

### Post by Super_6_4 on 2007-04-25
It looks to me like you'll need to load the drivers for you wireless card. Your paste there says you've got a Broadcom 1390 card.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell%20Wireless%201390](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell%20Wireless%201390)

check out this post. I have the same WLAN card, and this procedure worked right away. Hope it helps!:)

---

### Post by kpraytor on 2007-04-25
Ok, I tried to go the recommended page, and stuff started to go wrong on step 2. I typed "apt-get update" and this is what I got: 
"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

What does this mean?!?!?

---

### Post by Buffalo Soldier on 2007-04-25
> **kpraytor said:**
> I typed "apt-get update" and this is what I got: 
"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"
Basically it means some other program(s) is/are using apt repository list. Most probably you have a Synaptic Package Manager or Update Manager running at that moment. Shut down those applications and continue with the steps given in that guide.

Here's another guide that I found in the Community Docs. [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

---

### Post by kpraytor on 2007-04-26
Ok, I got a few more steps into the How To, but I ran into a problem when I implemented the code"sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist". It says "bash: /etc/modprobe.d/blacklist: Permission denied" I would really appreciate a little more help from anyone!

---

### Post by kyle_fransham on 2007-04-26
> **kpraytor said:**
> Ok, I got a few more steps into the How To, but I ran into a problem when I implemented the code"sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist". It says "bash: /etc/modprobe.d/blacklist: Permission denied" I would really appreciate a little more help from anyone!

Are you sure you appended the "sudo" before that command?  If so, an alternate way of doing the same thing is to:
```

sudo gedit /etc/modprobe.d/blacklist

```

and add the lines:
```

#This next line disables the loading of the bcm43xx module on startup
blacklist bcm43xx

```

save and close the file, and proceed with the other steps.

---

### Post by kpraytor on 2007-04-28
Ok, it took me 5 times to finally get my wireless working, but it works. Thanks to everyone who helped me so very much. 

I got one simple thing to anyone who is attempting to use the How To: It works, look at the poll. Don't get frustrated, it might take you a few times, and if you run into an error or something goes wrong, do a search within the thread. I found at least two or three other people who had the exact same errors and the problems were solved through the help of other people in the thread.

Almost every line of code that you have to implement is within the thread, and someone has had the exact same problem and there is an answer almost always soon to follow in the thread. Again, I just wanna thank everyone so very much for their patience and help!

---

### Post by kpraytor on 2007-04-30
Ok, After I had gotten everything to work on my computer, I went up to school (all my work to get the wireless up and running was done at home). I get up here to school, where they have an unsecured wireless network, and attempt to connect. My computer DOESN'T recognize my wireless card!!! It's like everything I had just done to get my wireless working was in vain. I type in "sudo ifconfig" and my computer only displays my wired connection and the loopback.

If anyone knows a good way to make surte this does not happen again, it would be greatly appreciated! I am wondering if I can do something with regards to putting into the command line of the kernel... that's just a guess. I am a newbie to all of this, so please have patience and take baby steps when explaining how to do something. Thank you very much, everyone, in advance for helping me out with this.

---

