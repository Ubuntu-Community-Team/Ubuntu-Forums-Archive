---
title: "installing a compatible wireless card"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by rorshach on 2008-02-09
so ive kind of given up hope of getting my wireless card to work with ubuntu, but i promissed myself im never going back to windows. as a result, i think im just going to buy a new wireless card. the only thing is...i dont know jack about where to start. im kind of hoping somebody can point me in the direction of a good tutorial on picking out and installing a compatible internal card.

any thoughts?

---

### Post by rustybronco on 2008-02-09
A few that I have experience with are in the links provided, the one that I am using at the moment is a wpc54gr pcmcia card that works well with hardy alpha 4 and wpa-tkip.
but as a general rule, pci bus devices are the easiest to get up and running.
[http://ubuntuhcl.org/pub/reviews.php?product_id=503](http://ubuntuhcl.org/pub/reviews.php?product_id=503)
[http://ubuntuhcl.org/pub/manufacturers.php?category_id=32](http://ubuntuhcl.org/pub/manufacturers.php?category_id=32)

also.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

It is probably best to know what kind of card you need (pci, pci-e, pcmcia, usb ect. ) then do a search for a compatible card and version (very imnportant) of that card. no hard and fast rule of finding what will work in ubuntu you just have to rely on what people have used and have gotten good results with.
what kind of encryption do you plan on implementing?, that also adds a variable to the list of cards available because some only can use wep.
*****edit***** internal card for a laptop, such as a pci-e mini? 
what does **lspci -nn** show for the card you have?, it should be possible to get what you have up and running,

---

### Post by rorshach on 2008-02-10
well, im not going to lie...im kind of a nub to a lot of this, so most of what you said kind of went over my head.  but i ran the command you told me to and this is what i got.


Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


i really appreciate the help...everyone here is seriously one of my favorite parts about this operating system.

---

### Post by rustybronco on 2008-02-10
> **rorshach said:**
> well, im not going to lie...im kind of a nub to a lot of this, so most of what you said kind of went over my head.  but i ran the command you told me to and this is what i got.

03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

I see by some of the posts you have made, you may have tried a few different methods to get your card to work. have you tried this method yet? [http://ubuntuforums.org/showpost.php?p=1140976&postcount=1](http://ubuntuforums.org/showpost.php?p=1140976&postcount=1) that should give you a couple of ways on getting your machine up and running. you could always download the files on a different machine then transfer them to your ubuntu installation via usb or a cd.
be sure to copy the commands **exactly** as posted (spacing and case)  

one other way would be to take your machine to someone that has a wired connection, then trying to enable the restricted drivers that are available through the restricted driver manager (this method) [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4) that would be simpler to try first.
I'l be in and out (family in the hospital) but still keeping an eye on this thread.

---

### Post by rorshach on 2008-02-10
i hadnt tried that...but i just did and now my internet is working flawlessly.  thank you so much...i REALLY appreciate it :)

---

### Post by rustybronco on 2008-02-10
Welcome to ubuntu!

---

