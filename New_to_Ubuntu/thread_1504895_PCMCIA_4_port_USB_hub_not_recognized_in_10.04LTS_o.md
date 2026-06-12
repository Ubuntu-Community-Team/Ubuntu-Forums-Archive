---
title: "PCMCIA 4 port USB hub not recognized in 10.04LTS or XP - Help"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by suomalainen on 2010-06-08
Ubunteros,

I just got this USB 2.0 Cardbus. It's a 32 bit PC card. It came with no drivers. I pluged it into the PCMCIA slot in XP and XP recognized it, said it installed the drivers and that it was ready for use but when any USB device was inserted nothing worked.

In Ubuntu 10.04LTS Nothing is see at all. Below I ran a lspci command. I can run otheres if needed.

Can someone help me with getting this card installed correctly.

Thank you very much!!!

> paul@paul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
03:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
paul@paul-laptop:~$ 


---

### Post by suomalainen on 2010-06-08
Daaaaa.......

There was a cable that is suppose to connect from the 
PCMCIA card to a empty USB port in back of the laptop now it's working.

---

### Post by blurpo on 2011-12-03
Hey suomalainen, I really, and I mean really, really appreciate you posting about this cable you had to connect.

It works for me now as well. :-)

Thanks man.

Surely there can't be anyone more stupid than me but let me explain just in case: I have a PCMCIA card that is a 4-port USB2.0 hub. I plugged it in and using lsusb, I see the hub. When I connect devices to the hub, they are not recognized. This is because the USB hub needs external power. It comes with a little cable that you can plug into the hub and the other end goes into one of the existing USB ports. If you do that, devices plugged into the hub will be seen (though it may take up to a minute, I've read).

---

### Post by suomalainen on 2011-12-04
Hey no problemo man!!!! And to think post is over year old....

---

