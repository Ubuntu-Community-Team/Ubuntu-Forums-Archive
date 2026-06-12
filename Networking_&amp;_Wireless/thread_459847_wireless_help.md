---
title: "wireless help"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by obavjestenja on 2007-05-31
my wireless work on xp,vista but on feisty no luck.
can you help guys but on simply it  language.
thanks.

---

### Post by FerhatBingol on 2007-05-31
First things to do

0) Check the "adding computer" to your wireless network process. I mean if you have to press on a button on the wireless router to except new members, did you do so?

1) Is your wireless hardware is recognized. Send us the output of "lspci" command which you will run under console mode. 

2) Check your wireless setup in windows, note down every info (type of security etc.) and check if they match with Ubuntu config.

3) Tell us more. "Wireless does not work" can be anything. Do you even see that computer tries to connect, or wireless option does not even come up, or does it say "it connected" but no data transfer. etc.

---

### Post by obavjestenja on 2007-05-31
> **FerhatBingol said:**
> First things to do

0) Check the "adding computer" to your wireless network process. I mean if you have to press on a button on the wireless router to except new members, did you do so?

1) Is your wireless hardware is recognized. Send us the output of "lspci" command which you will run under console mode. 

2) Check your wireless setup in windows, note down every info (type of security etc.) and check if they match with Ubuntu config.

my output:


00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 12)
08:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
08:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
08:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
08:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
08:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
pika@pika-laptop:~$

---

### Post by FerhatBingol on 2007-05-31
May I also learn what is the computer please? 

RaLink RT2500 mini PCI. I nevered used  a mini PCI on linux before, it might be interesting to read about it.

---

### Post by obavjestenja on 2007-05-31
> **FerhatBingol said:**
> May I also learn what is the computer please? 

RaLink RT2500 mini PCI. I nevered used  a mini PCI on linux before, it might be interesting to read about it.

LG laptop -- leso express

---

### Post by FerhatBingol on 2007-05-31
I think you are lucky.

The drivers have become opensource a while ago, and Ubuntu has a kernel module ready to setup at Synaptic Package Manager. 

Just set it up and let us know if it works.

Go to System/Administration/synaptec package manager and search for "rt2500".

---

### Post by obavjestenja on 2007-05-31
i instaled the drivers but,

i see the some wireless signal but i canot to connect to my network :(

please see the picture and helllllllllllllllllllllp:p


[[IMG]http://img400.imageshack.us/img400/2916/screenshotzr3.th.png[/IMG]](http://img400.imageshack.us/my.php?image=screenshotzr3.png)

---

### Post by FerhatBingol on 2007-05-31
fastest thing to do is to compare settings of XP and Ubuntu.

Open XP check your settings of wireless note down everything, do the same in ubuntu. Try to make them same as possible as it can.. and than we can continue from there...

---

### Post by obavjestenja on 2007-05-31
> **FerhatBingol said:**
> fastest thing to do is to compare settings of XP and Ubuntu.

Open XP check your settings of wireless note down everything, do the same in ubuntu. Try to make them same as possible as it can.. and than we can continue from there...

i delete xp from my laptop:(

---

### Post by FerhatBingol on 2007-05-31
there is no level of signal in tihs screenshot, is wireless ON from a button on the PC or something?

---

### Post by obavjestenja on 2007-05-31
> **FerhatBingol said:**
> there is no level of signal in tihs screenshot, is wireless ON from a button on the PC or something?

right now im connected true cable .
i don see the tht the wireless its on.

---

### Post by FerhatBingol on 2007-05-31
try without the cable. I am not good at this wireless usage maybe.

---

### Post by obavjestenja on 2007-05-31
> **FerhatBingol said:**
> try without the cable. I am not good at this wireless usage maybe.

without cable its no connection.
thanks for trying .

---

### Post by obavjestenja on 2007-05-31
why must be so hard to setup the wireless under ubuntu:(

---

### Post by FerhatBingol on 2007-05-31
well it worked for me out of the box. I am sorry that we could not manage yours. 

I advice you to read this page...

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

---

### Post by obavjestenja on 2007-05-31
ok, now have wireless bu i canot make to work  on roaming mode.
what that mean ?

[[IMG]http://img400.imageshack.us/img400/9607/screenshotco9.th.png[/IMG]](http://img400.imageshack.us/my.php?image=screenshotco9.png)

can this be fixed to work also on roaming mode ?

---

### Post by obavjestenja on 2007-05-31
so if my roaming mode not work i cannot connect to any wireless network outside ?

---

### Post by obavjestenja on 2007-05-31
any help :) ?

---

### Post by capn_hector on 2007-05-31
from what i have been reading, you dont NEED roaming mode.  if it works with out it i would not worry about it.

---

