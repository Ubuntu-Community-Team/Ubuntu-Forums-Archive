---
title: "Atheros + Acer Aspire 5043WLMi + Wifi = My doom"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by ZinkAlkon on 2008-05-28
**Acer Aspire 5043WLMi AMD Turion 64 bits Atheros 80211bcg, Ubuntu Hardy 8.04 64 bits**

I've been coming back and forth with this issue for quite a few days now, I travel a lot, so wired connections is not the answer for me :(

I've search, tried, retry almost every thread and post in here and the big ol' net... still nothing.

I've downloaded MadWifi drivers, my hardware module seems to be ok (orange light is always on) when I try to install the .inf file net5011.inf (that one is the one I need) even if I port it from WinXP, or locate it in the MadWifi extracted directory, gives me the following error: 

Unable to detect hardware

Funny thing, though, is that I hit OK, and shows nicely on the left side the .inf file and a nice Hardware detection: Yes. :confused:

Still unable to get it to scan anything, also tried unplugging the wired connection (dunno where I read that if u have it plugged, it won't pick up the wireless)... and as you can imagine, my frustration at this point is as big as it can get.
I also installed the Wicd app for scanning networks.

ANY ideas will be extensively appreciated (now I know there's a thank button somewhere...)

Again, thanks in advance to anyone that can help me, or at least will try, it's always nice to see people spending part of their time just helping others

---

### Post by ugm6hr on 2008-05-30
From the other thread - you have now installed ndiswrapper.  You don't need it.

If you can't get back to the equivalent of a fresh install, it may be difficult to work out what's going on.

If you want to post some more info, this thread tells you what is necessary:
[http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

---

### Post by ZinkAlkon on 2008-05-31
Oh, ok, thanks for the tip, I'll answer those questions one by one:

(coming from here) [http://ubuntuforums.org/showthread.php?p=5077089#post5077089](http://ubuntuforums.org/showthread.php?p=5077089#post5077089)

> **ugm6hr said:**
> From the other thread - you have now installed ndiswrapper.  You don't need it.

If you can't get back to the equivalent of a fresh install, it may be difficult to work out what's going on.

If you want to post some more info, this thread tells you what is necessary:
[http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

[B]
1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.[/B]

***Wifi connection***

**2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).**

[I][B]Acer Aspire 5043WLMi

System Type
    Notebook
Built-in Devices
    Stereo speakers, Wireless LAN antenna
Weight
    6.8 lbs
Localization
    United States
Notebook type
    Mid-size laptops (6-7.5 lbs.)
Screen type
    High-gloss/Anti-glare screen, Wide-screen
Wireless capabilities
    802.11g, 802.11b

Processor

Processor
    AMD Turion 64 mobile technology ML-32 / 1.8 GHz
64-bit processor
    Yes
Processor features
    AMD64 technology, PowerNow! technology, Enhanced Virus Protection, HyperTransport technology, Integrated memory controller
Chipset type
    ATI Radeon Xpress 200M

Cache Memory

Type
    L2 cache
Cache size
    512 KB

RAM

Installed Size
    512 MB - (added and extra 512 mb memory) = 1 gb
Technology
    DDR SDRAM - 333 MHz
Memory specification compliance
    PC2700

Storage Controller

Storage controller type
    IDE

Storage

Floppy Drive
    None
Hard Drive
    80 GB - 4200 rpm
Storage Removable
    None
Hard drive type
    Portable

Optical Storage

Type
    DVD±RW - Integrated

Optical Storage (2nd)

2nd optical storage type
    None

Display

Display Type
    15.4 in TFT active matrix
Max Resolution
    1280 x 800 ( WXGA)
Widescreen Display
    Yes
Color Support
    24-bit (16.7 million colors)
Features
    CrystalBrite

Audio

Audio output type
    Sound card
Audio Input
    Microphone

Input Device(s)

Input device type
    Keyboard, Touchpad, 4-way scroll button

Telecom

Modem
    Fax / modem
Max transfer rate
    56 Kbps
Protocols & Specifications
    ITU V.92
Modem features
    Wake on Ring

Networking

Networking
    Network adapter
Networking / Wireless LAN Supported
    Yes
Data link protocol
    Ethernet, IEEE 802.11b, IEEE 802.11g, Fast Ethernet, Gigabit Ethernet
Networking standards
    IEEE 802.11b, IEEE 802.11g

Expansion / Connectivity

Expansion Bays
    None
Expansion Slots Total (Free)
    2 ( 1 ) x Memory
Interfaces
    1 x Network - Ethernet 10Base-T/100Base-TX/1000Base-T - RJ-45, 1 x Modem - Phone line - RJ-11, 1 x Display / video - VGA - 15 pin HD D-Sub (HD-15), 1 x Audio - Line-in/microphone - Mini-phone 3.5 mm, 1 x Audio - Line-out/headphones - Mini-phone stereo 3.5 mm

Power

Power device form factor
    External
Voltage Required
    AC 120/230 V

Battery

Technology
    Lithium ion
Installed Qty
    1

Manufacturer Warranty

Service & support type
    1 year warranty
Service & Support Details
    Traveler warranty - Parts and labor - 1 year

Operating System / Software

OS Provided
    Microsoft Windows XP Home Edition [/B][/I]
[B]
3. Who is your Internet Service Provider (and in which country)?[/B]

Fibertel - Buenos Aires, Argentina

**4. Which version of Ubuntu are you using? e.g. Ubuntu 8.04, Xubuntu 7.10 etc.**

*Ubuntu 8.04 Hardy Heiron*
[B]
5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?
[/B]
*Yes I can, the ethernet connections works flawless, just plugged the cable in the back and worked like a wonder*
[B]
6. How are you getting online to post on this forum?[/B]

*My notebook, Ethernet connection*

7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.

Code:

lspci
lsusb
lshw -C network




zink@Zink-Book:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
zink@Zink-Book:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
zink@Zink-Book:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:0b:05:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,01/10/2004,4.0.0.14001 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:46:21:36
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.103 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes


Hope this works, let me know if there's anything else you might need in orders to assist me, so far, besides the Wifi Connection, I'm loving Ubuntu plus all the add ons, and I'm eager to learn how everything truly works! Thxs in advance

---

### Post by ZinkAlkon on 2008-05-31
Dunno where to answer this, so I did it here

[http://ubuntuforums.org/showthread.php?p=5082726#post5082726](http://ubuntuforums.org/showthread.php?p=5082726#post5082726)

Hope this works out:D

---

### Post by ugm6hr on 2008-05-31
Just confirming some details there:
```
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```
```
*-network:0 **DISABLED**
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 5
bus info: pci@0000:06:05.0
logical name: wlan0
version: 01
serial: 00:16:cf:0b:05:2a
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=**ndiswrapper**+net5211 driverversion=1.52+,01/10/2004,4.0.0.14001 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```
OK. Your card will work.  It is identical to mine, in a very similar laptop.

Unfortunately, as stated in your own thread, you have modified the drivers.  I can't help without knowing *exactly* what you have done (or if you do a fresh re-install).  This is because from a fersh install your wifi will just work.  Having modified the driver choice to include ndiswrapper, you have changed this.

Also - did you check the comment re: Windows dual-boot?

PS: I have moved both posts to your own thread to ensure it is in the current forum.  Please continue in your own thread.

---

