---
title: "Ubuntu &amp; wireless"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by vanzan on 2007-07-02
I know nothing about Linux but I was using Ubuntu as a Live CD last night to see what all the fuss is about. I must say I am impressed! The main problem was I couldn't connect to my Eircom wireless internet. I tried entering my SSID and passphrase but nothing happened.

I was tinkering with System - Administration - Network turning off roaming and on again...just basically trying everything turning it off and on but I just couldn't get surfing. I have a Dell Wireless 1370 WLAN Mini PCI Card.

Any one out there scale this obstacle before me?

---

### Post by richardjennings on 2007-07-02
I think the Dell Wireless 1370 WLAN Mini PCI Card uses a broadcom chipset.

you can check this by using the command " lspci " in a terminal.

that command lists all of you pci cards and shows a little information about them.

can you post the output from lspci

---

### Post by vanzan on 2007-07-02
errrm I'll do that but how can I get the information pasted into a post? I can't connect to the internet with ubuntu and AFAIK can't write to the ntfs HD....guess its a pen and paper job!

*edit* somehow managed to use a usb drive...worked more by luck than anything.

---

### Post by vanzan on 2007-07-02
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by kevdog on 2007-07-02
You will be able to connect to internet with the use of ndiswrapper (which is not included on the install cd).
Do you have the windows drivers for your wireless card -- ndiswrapper will need these?

---

### Post by vanzan on 2007-07-02
erm the windows drivers for my wireless card? I got some cd's with my laptop but I also got a cd from my wireless broadband provider...I don't know which the drivers would be on? What do I do once I get them? Is there a guide? Thanks for the help!

---

### Post by kevdog on 2007-07-02
Lets just ndiswrapper installed properly and then we will find the drivers. If anywhere they would be with the disks that came with your computer.

Put ubuntu cd in driver and wait to spin up
Using command line:
1. sudo apt-cdrom add
2. sudo aptitude update
3. sudo aptitude install build-essential

cd ~
mkdir ndiswrapper
Using a different computer that you have a internet connection on download ndiswrapper-1.47.tar.gz from: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482).  Place this in the ~/ndiswrapper directory

Now lets decompress the archive:
cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47

Compile and install:
make distclean
make
sudo make install

Check if ndiswrapper is installed correctly with 
ndiswrapper -v

Please post the output from the above command.
I'll wait for you to catch up.
The next step is dealing with the windows drivers.

---

### Post by vanzan on 2007-07-02
I'm a little confused sorry....where do i type

1. sudo apt-cdrom add
2. sudo aptitude update
3. sudo aptitude install build-essential

in a terminal?

then I type 

cd ~ mkdir ndiswrapper

in a terminal as well?

---

### Post by darrenm on 2007-07-02
Just another point of view here, don't mean to butt in.

If you are unlucky enough to be saddled with an AirForce1 then I would recommend you to do what I did, bin it and buy an Intel 2200BG for about £15/$30 from eBay/* then wireless will work perfectly. Intel release specifications and drivers for Linux, Broadcom are a useless anti-Linux company that make cheap products.

You can get the Broadcom working using Windows drivers and NDISwrapper or if you are lucky bcm43xx which is the reverse engineered Linux attempt at a driver but it will be a lot of work.

Personally I could never get on with NDISwrapper. I installed a package called bcm43xx-fwcutter which grabs the firmware for the card off the internet for you. If you have a wired ethernet connection you can use then you can run Synaptic and search for that package then you may be lucky. I got it working like this then swapped to Intel and never looked back.

Good luck, :)

---

### Post by vanzan on 2007-07-02
yeah its a lot of work...a shame really because I was really impressed with ubuntu and it takes a lot to impress me, bitter cynic that I am. Looks like cheaping out on a Dell has done me :(

---

### Post by kevdog on 2007-07-02
Just type all the commands in a terminal.  Installing ndiswraper isnt all that hard and plus you will learn something about your system as well.  If you think linux is windows, then your sadly mistaken.  This doesnt mean things are harder in linux (wireless would be an exception to this rule), however things are installed a lot differently.

---

### Post by hiway on 2007-07-02
I beg forgiveness for butting in...

I was following along as I needed to install ndsiwrapper as well, and this thread was the one I ended up on after starting my own that went unanswered. 

When I typed sudo aptitude update- I was told the "dpkg" was interrupted and I need to run it manually.  --configure -a' to correct the problem. Couldn't rebuild package cache.

I am a total rank amateur with linux.... but I learn fast! Any help on this? Please?

---

### Post by kevdog on 2007-07-02
Im not sure, try typing 

sudo dpkg --configure a

at command line.

---

### Post by hiway on 2007-07-02
no package named a is installed, cannot configure....?

It's all linux to me man.... but I can follow instructions

---

### Post by hiway on 2007-07-02
OOPS! needed the "-" before the a...it's working now.... loading something I am supposing.

---

### Post by hiway on 2007-07-02
I should mention that ndiswrapper and my linksys driver for the pcmia card are on my desktop... with that said, any help on whats next? Previous error is resolved.

And what in the world are super cow powers? lol!

---

### Post by hiway on 2007-07-03
I found the cheapest and easiest alternative.... $39 and a trip to ciruit city got me this netgear wg511t pcmia card and I am hittin and stickin like popeye's chicken!

... still would like to know what "Super Cow Powers" are...

---

### Post by kevdog on 2007-07-03
Yea, a lot of people should do what you just did.  Anyway can you post the following for me, I just want to know more about your card:

lspci
lshw -C network

Thanks

---

### Post by hiway on 2007-07-03
;lspci:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420
02:01.1 CardBus bridge: Texas Instruments PCI1420
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

-C network:
*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:d9:00:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@07:00.0
       logical name: wifi0
       version: 01
       serial: 00:18:4d:95:37:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.104 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:2c000000-2c00ffff irq:11

I believe this is what you were asking for?

---

### Post by kevdog on 2007-07-03
So what your post tells me that the 

netgear wg511t pcmia card (product name)
Atheros Communications, Inc. AR5212 802.11abg NIC  (chipset)
driver=ath_pci (driver)

works out of the box with Ubuntu.  Hmm, I didnt know this.  Thats great..Im going to have to remember this one!

---

### Post by hiway on 2007-07-03
I'll go ya one better dog... the cheapo usb optical mouse for notebooks ($15- NX [circuit city store brand]) is another out of the box cheap fix for the erratic mouse issues with the older Dell lappys.

I am just chock full of great finds today!

---

### Post by t4thfavor on 2007-07-04
All you have to remember is that any wireless card that isn't broken, and has the word "Atheros" in the name will work out of the box with no tweaking,

Broadcom on the other hand is a no-go usually. I got mine to go with the fwcutter tool, and the windows driver (to extract the firmware from). 

To get the windows driver you can download the exe from dell which just unpacks it to a temp folder. =, You will need the .sys file.

---

### Post by vanzan on 2007-07-04
Calling kevdog! OP here! I finally got around to doing what you told me and this is what I got after ndiswrapper -v:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586

Can you tell me what to do next? I've found my DELL drivers cd also! Since I typed what you told me while running as a LiveCD and have had to log off to get back to XP and the internet, I assume I'll have to type it all again?

Did the other poster here, hiway, buy a different wireless card? I got a little confused by his post. Is that what generally most people do with a Broadcom? I am wary of this because I don't know anything about replacing my wireless card on my laptop and suspect it would be difficult. 

Thanks again kevdog.

---

### Post by hiway on 2007-07-04
> **vanzan said:**
> ...
Did the other poster here, hiway, buy a different wireless card? I got a little confused by his post. Is that what generally most people do with a Broadcom? I am wary of this because I don't know anything about replacing my wireless card on my laptop and suspect it would be difficult. 
....

I had an old dell C610 with a PCMIA slot... no integrated wireless card- and I just went out and purchased an inexpensive card that is plug and play... to use a windows term.... pleuuuughech!

---

### Post by kevdog on 2007-07-04
Great.

Put the wireless drivers (I believe the Windows XP drivers in a folder -- for example ~/driver.  This folder should contain at minimum a ****.sys and ****.inf file

Then do the following
cd ~/driver
sudo ndiswrapper -i *****.inf
Check if everthing is OK
ndiswrapper -l

sudo depmod -a
sudo modprobe ndiswrapper
Check if everything is OK
dmesg | grep ndiswrapper <---Make sure no errors

sudo ndiswrapper -m

Please post at this point after a reboot, the output of 
lshw -C network

It might work at this point, however usually a few more steps need to be done.  Make sure on the router there is no WPA/WEP or MAC filtering (we can turn this stuff on later).

---

### Post by vanzan on 2007-07-04
> **kevdog said:**
> 

Please post at this point after a reboot, the output of 
lshw -C network

You say "after a reboot" but I'm running it only as a Live CD ...won't everything be lost after a reboot?

> **kevdog said:**
> 
It might work at this point, however usually a few more steps need to be done.  Make sure on the router there is no WPA/WEP or MAC filtering (we can turn this stuff on later).

God I've no idea whether my route has WPA/WEP or MAC filtering....I know I had to enter a WEP passphrase when I first set it up with XP. Anyway I'll try what you've said tomorrow...thanks for your patience and help sir!

---

### Post by kevdog on 2007-07-05
Never setup ndiswrapper on a liveCD.  Maybe it would work - Im not sure.  Better to ask in the forums if someone has done this.

---

### Post by darrenm on 2007-07-05
```
sudo rmmod bcm43xx && sudo rmmod ndiswrapper && sudo modprobe ndiswrapper
``` should be fine without rebooting.

---

### Post by vanzan on 2007-07-05
I input that after doing what kevdog told me to input? Crikey I have no clue what those commands mean...

---

### Post by darrenm on 2007-07-05
yes and it should magically make your wifi light start flashing. Then the network manager icon should work as normal.

---

### Post by walkerk on 2007-07-05
> **darrenm said:**
> Just another point of view here, don't mean to butt in.

If you are unlucky enough to be saddled with an AirForce1 then I would recommend you to do what I did, bin it and buy an Intel 2200BG for about £15/$30 from eBay/* then wireless will work perfectly. Intel release specifications and drivers for Linux, Broadcom are a useless anti-Linux company that make cheap products.

You can get the Broadcom working using Windows drivers and NDISwrapper or if you are lucky bcm43xx which is the reverse engineered Linux attempt at a driver but it will be a lot of work.

Personally I could never get on with NDISwrapper. I installed a package called bcm43xx-fwcutter which grabs the firmware for the card off the internet for you. If you have a wired ethernet connection you can use then you can run Synaptic and search for that package then you may be lucky. I got it working like this then swapped to Intel and never looked back.

Good luck, :)

its hardly a lot of work. i have a broadcom 1390 and i use ndiswrapper with ease. i used [wicd]("http://wicd.sourceforge.net") to connect to the internet..

for ndiswrapper just search for 'broadcom wireless' within the forum...  ([heres a good guide]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+wireless"))

don't waste your money..

---

### Post by vanzan on 2007-07-05
It didn't work. In fact the "wireless" section under Network was removed altogether. I tried Firefox but there was no connection. I entered all the commands kevdog listed and then darrenm's command.

Also I ran into trouble when I tried to get the drivers from the DELL cd that came with my laptop. There were Chip Set Drivers, Communication Drivers, Input Drivers, Video Drivers and Network Drivers.

I looked under the "Network Drivers" section and oh no there was 5 different types:

1. Broadcom 440x 10/100 Intergrated Controller Rev: A13
2. Dell_Wireless (Except US, Japan) WLAN Network Adapter Card Rev:A07
3. Dell_Wireless (Japan) WLAN Network Card Rev: A07
4. Dell_wireless (US) WLAN Network Card Rev:A07
5. Intel (R) PRO/Wireless Network Connection Rev:A10

I went with the first one and there was 3 files in the XP folder within: b44win.inf, b44win.cat, bcm4sbxp.sys

Were these the correct ones?

---

### Post by darrenm on 2007-07-05
> **walkerk said:**
> its hardly a lot of work. i have a broadcom 1390 and i use ndiswrapper with ease. i used [wicd]("http://wicd.sourceforge.net") to connect to the internet..

for ndiswrapper just search for 'broadcom wireless' within the forum...  ([heres a good guide]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+wireless"))

don't waste your money..

I've been there and done that with the Broadcom stuff. Even when you do get it working its hit and miss. If you have a kernel update you have to recompile the ndiswrapper module unless you use a package. My light stayed on permanently and didnt flash and I got poor performance. I bought an Intel 2200BG for very little money and all these problems are gone. Different people have different experiences and it all differs vastly between revisions of the chips. For some people it will be a lot of work. I'm glad you had a good experience.

---

### Post by vanzan on 2007-07-05
that installer in the thread walkerk linked to worked a treat! I'm posting this from Firefox on Ubuntu! Hurray!

---

