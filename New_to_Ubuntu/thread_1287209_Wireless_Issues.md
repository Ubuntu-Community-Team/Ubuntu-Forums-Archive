---
title: "Wireless Issues"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by crazypao on 2009-10-09
I am super new to linux. I installed last night because my Windows XP finally bit the big one [little brother got on... virus... you know] So in order to get my lappy back, I had to reformat. [I do not have a Windows Boot CD] Anyways, so now Ubuntu is all I have on my computer. Everythings great, except I can not access the internet. I have tried the troubleshooting, but nothing, I'm not able to turn on my broadcom network adapter. Just wont turn on. I don't know what to do next, and I don't really want to have to buy a new lappy. 
 
Anybody have any helpful tips?
 
P.S. I don't know much really about the whole "Terminal" thing. I've been looking through here trying to learn, but I don't quite get itplease explain in a way I might understand. 
 
Thanks.

---

### Post by crazypao on 2009-10-09
Bump

---

### Post by fidelandche on 2009-10-09
I cannot provide any information about your problem, but have you tried Google?? This comes up with many answers. Also have you tried looking at the network section of the forum??
 
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
 
 You also need to provide what laptop you are using, version of Ubuntu and details of the problem in more detail and more details on the router, the help to provide that information is in the network section as above in the stickies.
 
Also remember that everybody on this forum gives their time and help for free, so please be patient while waiting for a reply.

---

### Post by allenbradley on 2009-10-09
Do this: Press Alt+F2. A run dialog should pop up. Type in ```
gnome-terminal
```and press enter. A window should appear, with a prompt ( this is the terminal emulator ). Now, type ```
lspci
``` and post the output here.

---

### Post by crazypao on 2009-10-10
This is what showed up.
 
christina@Lappy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by ConXtionS on 2009-10-10
I feel for ya bro

I dont have a solution except to say that getting a copy of xp is not a HUGE problem and is cheaper than another lap top.

Also, there are lots of different wireless adapaters to use... that dont cost much either...

GOod luck on this

Jim

---

### Post by sukigenseki on 2009-10-10
For my broadcom wireless, which is the bcm 4311 I had to go to system - administration - hardware drivers, and choose the Broadcom STA Wireless driver to enable. That is the same one that your wireless will use as well. Your wireless network hardware will not work without that installed. The second option is to do

sudo apt-get install b43-fwcutter

in a terminal (make sure your computer is plugged in to a lan to still get internet access) and that will download the firmware for your card, but i would seriously recommend the first one the most. First option should be pretty cut and dry and hassle free.

---

### Post by OlsenCNC on 2009-10-10
That's strange. I have the same adapter, and it worked after a clean install with no modifications. I'm sure you have already done this, but have you checked the physical switch on the laptop to ensure that it is enabled? 

~mike

---

### Post by sukigenseki on 2009-10-10
You know olsen now that I think about it that is the first thing that happened to me. I didn't realize that I simply needed to use the fn+f2 key which is my wireless key on my dell laptop to just turn the thing on. I went through like 30 minutes of being boggled before I realized I had just not turned on my wireless yet lol.

---

### Post by bkratz on 2009-10-10
> **crazypao said:**
> I am super new to linux. I installed last night because my Windows XP finally bit the big one [little brother got on... virus... you know] So in order to get my lappy back, I had to reformat. [I do not have a Windows Boot CD] Anyways, so now Ubuntu is all I have on my computer. Everythings great, except I can not access the internet. I have tried the troubleshooting, but nothing, I'm not able to turn on my broadcom network adapter. Just wont turn on. I don't know what to do next, and I don't really want to have to buy a new lappy. 
 
Anybody have any helpful tips?
 
P.S. I don't know much really about the whole "Terminal" thing. I've been looking through here trying to learn, but I don't quite get itplease explain in a way I might understand. 
 
Thanks.



Please look at this thread  [http://ubuntuforums.org/showthread.php?t=1139412](http://ubuntuforums.org/showthread.php?t=1139412)
it seems like these gentlemen solved the same situation.

Good luck!

---

