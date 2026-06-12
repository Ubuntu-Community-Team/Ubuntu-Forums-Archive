---
title: "No wifi on IBM T30"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by headfirst_for_halos on 2010-03-20
Hello everyone
I recently switched to Ubuntu and everything has been really good except for one thing, I can't get my wireless network to connect.

I've followed the instructions of this thread [http://ubuntuforums.org/showthread.php?t=867947&highlight=Cisco+Aironet+Wireless+802.11b](http://ubuntuforums.org/showthread.php?t=867947&highlight=Cisco+Aironet+Wireless+802.11b) But It still doesn't work

So, according to that thread, Is my file supposed to be like the one in the attachment or do I have to change something?

EDIT:

Computer specs:

+Ubuntu 9.10 installed 
+windows xp installed (in another partition of course)

---

### Post by louieb on 2010-03-20
What type of card? internal or external?
If internal make sure its seated properly?
please pot the output of 

```
lspci
```

I have a T30 also - Intel internal wireless card - wireless works out of the box.

---

### Post by headfirst_for_halos on 2010-03-20
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: **AIRONET Wireless Communications Cisco Aironet Wireless 802.11b**
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
```

It's an internal card and the computer knows it's there but for some reason it is not working

---

### Post by hictio on 2010-03-20
Are you editing the file as the user root, right? Using sudo?
I have a T43, and the WiFi worked right from the beginning.

What it is the problem? You can't connect to an Access Point for instance? Or you can't even get an IP address?

---

### Post by headfirst_for_halos on 2010-03-21
> **hictio said:**
> Are you editing the file as the user root, right? Using sudo?
I have a T43, and the WiFi worked right from the beginning.

What it is the problem? You can't connect to an Access Point for instance? Or you can't even get an IP address?

Yes, I'm editing it as root otherwise I can't edit it.
the problem is that I don't have the option to connect to a wireless network (see the attached image)

--------------------------------------------------------------------------
Thanks everyone for taking time to help me solve this problem :)

---

### Post by louieb on 2010-03-21
Don't have much time right now. But here are 2 good places to look.
[ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki") 
[ThinkPad Forum ]("http://forum.thinkpads.com/") 

Took a quick look The Cisco card should work - the driver is built in to the 2.6 kernel. ThinkWiki has a link to IBM's Linux wireless page too

---

### Post by headfirst_for_halos on 2010-03-21
Thanks for the links but sadly they didn't help me to solve the problem

---

