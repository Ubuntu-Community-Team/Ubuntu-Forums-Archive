---
title: "How do I install a linksys WPC54G v4 network PCMIA card on xubuntu?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by emailstimpy on 2007-08-30
How do I install a linksys WPC54G v4 network PCMIA card on xubuntu? Is it possible? I am very new to Linux. I don't know how to do much of anything; so please be as specific as possible. Step by step would be great. Assume I know nothing about computers.

---

### Post by dmizer on 2007-08-30
go to a terminal:

applications > accessories > terminal

type:
```
lspci
```
and hit <enter>

paste the output in this thread.

if you do not have internet connection at all, please save the output to a text file, and transfer it to another computer via usb drive or similar method.

also post what version of ubuntu you have installed.  you can determine this by going to:
system > about ubuntu
and look for the sentence that begins, "Thank you for your interest in Ubuntu ..." what follows is your ubuntu version (most likely dapper, edgy, or feisty).

this will give us part of the information we need to help you get your card working correctly.

---

### Post by emailstimpy on 2007-08-30
Thank you for responding,BTW. 

Here are the results of the lspci.

00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
00:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)

I am running xubuntu 7.04 Fiesty on a Compaq that is damn slow.

---

### Post by dmizer on 2007-08-31
humm ... was the card inserted when you performed the lspci command?

---

### Post by emailstimpy on 2007-09-01
Here it is with the card plugged in.

00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
00:0b.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade i1 (rev 6a)
02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

I wasn't aware that the card had to be in.

---

### Post by dmizer on 2007-09-01
sorry, my fault for not being specific enough.  okay, your card's chipset is INPROCOMM IPN 2220, and it might be tricky to get it working (if you want to look for howto's on your own, you should search for INPROCOMM IPN 2220).

can you get wired internet connected with that computer?

this post contains the best information i've found for how to get it to work: [http://ubuntuforums.org/showpost.php?p=113584&postcount=7](http://ubuntuforums.org/showpost.php?p=113584&postcount=7) let me know if you need help with that.

---

### Post by emailstimpy on 2007-09-02
I totally appreciate it. I got it all to work! Yeah!

---

### Post by radaps60 on 2008-07-21
does this work with the xbuntu 8.04.1 release?

---

### Post by dmizer on 2008-07-22
> **radaps60 said:**
> does this work with the xbuntu 8.04.1 release?

i don't know why it wouldn't.  you could always try the live cd for testing.

---

