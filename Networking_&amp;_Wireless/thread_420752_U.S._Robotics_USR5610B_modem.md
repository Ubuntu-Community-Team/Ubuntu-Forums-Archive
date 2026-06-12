---
title: "U.S. Robotics USR5610B modem"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by David Ostrom on 2007-04-23
Hello,
I’m hoping someone can help me connect to the internet. I have Ubuntu 7.04 Feisty with a newly installed U.S. Robotics USR5610B modem. The modem dials up my provider but when I click on the Firefox browser, nothing happens and then it disconnects.
Can someone give me a step by step being I’m new to Ubuntu and Linux.
Thank you in advance,
David Ostrom

---

### Post by unisol on 2007-04-23
what software do you use to dial up ? what port is your modem set at?

---

### Post by David Ostrom on 2007-04-23
Does Ubuntu come with software for dialing up? I’ve been dialing in thru network setting. My network is set at (I’m guessing port?) /dev/ttys2, port on windows is com3.
Does this help?
Thanks,
David

---

### Post by David Ostrom on 2007-04-24
Here is my system information.


david@davids-computer:~$ lspci 
00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 02) 
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller 
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4) 
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] 
00:0a.0 USB Controller: NEC Corporation USB (rev 43) 
00:0a.1 USB Controller: NEC Corporation USB (rev 43) 
00:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04) 
00:0b.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) 
00:0c.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06) 
00:0d.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04) 
00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10) 
00:10.0 RAID bus controller: Silicon Image, Inc. SiI 0649 Ultra ATA/100 PCI to ATA Host Controller (rev 01) 
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) 
david@davids-computer:~$

---

### Post by Michl on 2007-05-03
I believe this is a bug.  I just installed Feisty on a machine with the very same modem
and I keep getting disconnected, whether using Admin-Network or wvdial. 

I have been using this modem on two machines with 6.10 with success, so none
of the standard responses are going to help here.  All the proper init2 commands
are added, including S19=0, and I have compared it to the strings on the
edgy machine as well as win2k, etc.

If you look at the log, it seems like there is an error in PPP so that the PPP
daemon keeps dying for some reason.

My theory is that in Edgy System->Admin -> network the modem did not
work.  That is a confirmed bug on the launchpad.  The alpha and beta
editions of Feisty had the same problem and there was some pressure to
have this fixed.  Well, someone tried to fix it and this is worthy of praise,
E for Effort, but they made a complete mess of dial-up in Feisty.  I will
check the launchpad on this, but unless someone has a quick fix for this,
I will be reinstalling Edgy.

I have to say, may relation to ubuntu is love/hate.

---

