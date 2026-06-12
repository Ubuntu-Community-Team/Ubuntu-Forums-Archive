---
title: "Hp dv1000 in kubuntu 6.06 i see the network but can't connect"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Frixhias on 2006-09-06
I installed kubuntu 6.06, and the most of thing works pretty well, so far this issue stop me to leave windows and migrate to linux on my laptop. I can't connect to my wifi network is works well by LAN, but not WLAN. Kubuntu recognize the network (Friz-Bravo-Network) i put the WEP key but still show me didn't connect like the picture below

[[img]http://img3.freeimagehosting.net/uploads/th.b56dab54b5.png[/img]](http://img3.freeimagehosting.net/image.php?b56dab54b5.png)


Before kubuntu i test SUSE 10.1 in this even the connection to WPA works fine with the knetworkmanager is that why i think is only problem to configuration or driver but not the hardware.

I install the automatix and de laptop wifi option, not work.
I try to install knetworkmanager with 

$sudo aptitude install knetworkmanager
and
$apt-get install knetworkmanager

but i can't.

In this image you can see the laptop show me both cards.

[[img]http://img3.freeimagehosting.net/uploads/th.8b5a2f29ee.png[/img]](http://img3.freeimagehosting.net/image.php?8b5a2f29ee.png)

Any idea? please don't assume to much i'm pretty newbie and I'm sorry for my poor english.

To use WPA the only way is with knetworkmanager?

Thanks for your time.

---

### Post by Frixhias on 2006-09-06
Please, anything helps me, I really don't know what to do, read this or something :mrgreen:

---

### Post by haiku99 on 2006-09-07
check out the howto's at [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
also, you need to find out what brand and model your wifi card is before proceeding, type lspci in a terminal window and it should tell you...

---

### Post by Frixhias on 2006-09-07
First I want to thank you for your answers   I'm really "desesperated" with this right   now, because i don't know what to do.    This the lspci show me    > root@frixhias:/home/frixhias# lspci
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc
essor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc
essor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated
 Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphi
cs Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4
-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4
-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4
-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH                                                                                                   CI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg                                                                                                   e (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (                                                                                                   rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus                                                                                                    Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH                                                                                                   4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97                                                                                                    Modem Controller (rev 03)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                                                                                   /8139C+ [B](rev 10)
0000:02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)[/B]
0000:02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho                                                                                                   st Controller
0000:02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash                                                                                                   Media Controller
0000:02:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411                                                                                                   , PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
root@frixhias:/home/frixhias#
    

In black my wifi card, i previosly read a couple of post to how to   remove old driver (i do this a few days   earlier and i to make reainstall :S)    

If i see the card this is not indicate to   works? because i see my network, but   says "connection failed" and no reports to   any error.    I think if i know the error maybe can i fix   it, but only say "connection failed"

I'll read your link

Thank you haiku99

********Edited********

Without a key i mean open network connected             perfect, hardware or problem of driver             are out with this, but how can i connect             with key (WEP or WPA) still is a mystery   for my :-k

---

