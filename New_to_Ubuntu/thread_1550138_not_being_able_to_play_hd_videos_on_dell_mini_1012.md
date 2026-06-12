---
title: "not being able to play hd videos on dell mini 1012"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-10
using lynx.


I have some 720p HD videos and when i  try to play them they dont play smoothly. almost unwatchable, its like buffering from the internet, what can be the reason for that? i think i have to enable 3d acc. or sumthing,. any ideas?

---

### Post by jtarin on 2010-08-10
What video card/chip do you have?
I use VLC player for all my video viewing. Plays all formats.

---

### Post by fremantle on 2010-08-10
ya i got vlc.

this is what sysinfo shows 

VGA Controller
Intel corporation n10 family integrated graphics controller


* i bought the dell  mini 1012 that DOES not have hd. the hd one was like 50-60 dollars moar


i think the driver is installed. compiz and everything is running smooothly

---

### Post by snowpine on 2010-08-10
Does switching Compiz off make a difference?

---

### Post by fremantle on 2010-08-10
does :no effects" stop compiz?

---

### Post by snowpine on 2010-08-10
> **fremantle said:**
> does :no effects" stop compiz?

Yes, it should. :)

---

### Post by fremantle on 2010-08-10
no. not working. plzzz plz plz someone help me out :(( i even watched hd 720p on my dell d600 so why cant i do it in mini 1012??

---

### Post by jtarin on 2010-08-10
Do you have the space to copy the movie to your computer? I'm afraid that with your setup (amt. of memory and no drive) you have not enough buffer to load the dvd to. This allows for smoother uninterrupted streaming.How large did you make your swap space? Try copying it and see what the resukts are, then we can go from there.

---

### Post by jtarin on 2010-08-10
I found this about your Mini:
> It does matter which media player a user chooses, though. We tried Windows Media Player 12, Media Player Classic, CyberLink's Power DVD, DivX Player 7.0 and the VLC Player 1.0.3. HD coded YouTube clips only ran on Windows Media Player 12/Classic and Power DVD 9.0 consistently smooth. The screenshot shows that the Atom processor is only loaded between 28 (720p) and 41 percent (1080p) at the same time.

The players from DivX and VLC weren't able to render the clips smoothly and also created intense Pixel errors. Even CyberLinks older Power DVD 7.0 only played the clips very juttery, even if without Pixel errors. In short: The Broadcom Crystal HD chip allows for smooth HD on the netbook. The suppliers of a few software players still have to incorporate the use of Crystal HD. However, HD decoding already works great with commercial players from Microsoft and CyberLink.

---

### Post by jtarin on 2010-08-10
There is another possibility.....compiling a driver from Broadcom.
> Linux Software

To encourage the development of Linux media player applications using our HD video decoders, Broadcom is releasing the Linux kernel driver source code under the GNU General Public License (GPL), version 2 as well as application and library source code on a royalty-free basis under the GNU Lesser General Public License (LGPL), version 2.1, as published by the Free Software Foundation.

[Current driver source supporting all kernels >= 2.6.11 (07/03/2010)]("http://www.broadcom.com/support/crystal_hd/")

    * Download Crystal HD driver source

Broadcom's BCM70012 and BCM70015 are supported.

Issue the command in your terminal ```
lspci
``` and lets see what chip you have.

---

### Post by fremantle on 2010-08-10
> **jtarin said:**
> There is another possibility.....compiling a driver from Broadcom.

Broadcom's BCM70012 and BCM70015 are supported.

Issue the command in your terminal ```
lspci
``` and lets see what chip you have.

> 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


thats the output...

---

### Post by fremantle on 2010-08-10
i do not think my graphics card is broadcom.

---

### Post by fremantle on 2010-08-10
can i run powerdvd under wine? i have a copy of that.

---

### Post by jtarin on 2010-08-10
> **fremantle said:**
> can i run powerdvd under wine? i have a copy of that.
[Possibly.]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1822")

---

### Post by Terl on 2010-08-10
> **fremantle said:**
> 


* i bought the dell  mini 1012 that DOES not have hd. the hd one was like 50-60 dollars moar


Hmm, I think this may be the issue?  You clearly said does NOT have the HD monitor....

---

### Post by jtarin on 2010-08-10
I agree....I was originally reading HD as hard drive. Maybe you can possibly upgrade. Take it back and tell them it was the wrong one they gave you. You asked for the HD one.It's worth a shot.

---

### Post by fremantle on 2010-08-11
hm but how come 720p videos played smoothly on my dell d600? it didnt hav hd graphics either.

---

### Post by jtarin on 2010-08-12
It came with a ATI GPU Radeon 9000...Do you know anything about the equipment you have or is it your habit to install blindly any operating system to any hardware and are mystified that it doesn't work? You should actually learn something about your own equipment.

---

### Post by fremantle on 2010-08-12
its my habit

---

