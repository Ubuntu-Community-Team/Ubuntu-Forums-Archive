---
title: "Wireless Connection Problems"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by XJRodzx on 2008-05-01
Ive installed Gutsy on my Compaq Presario M2000 and had the wireless working great.

Now I upgraded to Hardy Heron (Clean Install), and I seem to b having problems connecting to my wireless network.

I followed the guide posted [here]("http://ubuntuforums.org/showthread.php?t=684495") but I get this message after my attempt on an Unencrypted connection.
```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Any help is much appreciated.

---

### Post by Ayuthia on 2008-05-02
Can you post your lspci -nn?  It will help us know which wireless card you have.  Thanks!

---

### Post by pseudo-random on 2008-05-02
In terms of communication layers you've got the main layers ok (Physical and Data link) It's just a case of getting an IP (layer 3) and you're there.
In your case you're asking for one automatically but you could assign yourself one ```
sudo ifconfig ath0 192.168.0.2
``` for example.
Then add your gateway (assuming 192.168.0.1 is router)
```
sudo route add default gw 192.168.0.1
```
Then your DNS in /etc/resolv.conf
```
nameserver 192.168.0.1
```

---

### Post by XJRodzx on 2008-05-02
Ayuthia

```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [:0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
```


pseudo-random:

Im still a Ubuntu/Linux noob so Im not sure exactly what I needed to do with what you posted for me.

Thanx to both of you for the responces, hopefully we can get this resolved soon.

---

### Post by Ayuthia on 2008-05-02
> 02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
In case you did not know, this is your wireless card.  There is a change in how Broadcom drivers work in this new kernel (2.6.24).  The driver has changed from bcm43xx to b43.  

Do you recall how you got your wireless working in Gutsy?  You had two options in Gutsy--install bcm43xx-fwcutter or use NDISwrapper.  If you don't recall, I am going to guess that you used bcm43xx-fwcutter because most people remember installing NDISwrapper because there are several steps to it.

If you want to try the native Linux module first, you can install b43-fwcutter.  Another way would be to try the Hardware Restricted Manager.  I am not for sure where it is located in your menu because I am a KDE user.  It will ask you if you want it to find a driver for you.  If you want it to, you will need to make sure that you have a working internet connection or else it will get stuck.

---

### Post by XJRodzx on 2008-05-02
> **Ayuthia said:**
> Do you recall how you got your wireless working in Gutsy?  You had two options in Gutsy--install bcm43xx-fwcutter or use NDISwrapper.  If you don't recall, I am going to guess that you used bcm43xx-fwcutter because most people remember installing NDISwrapper because there are several steps to it.

If you want to try the native Linux module first, you can install b43-fwcutter.

Well in Gutsy all I did was enable the restricted driver, and made a new wireless connection. At the top pannel on the right side theres a network thing where I can make changes. Thats where I connected from in Gutsy.

I tried the exact same thing in Hardy but it didnt work.

I tried installing b43-fwcutter and it said:
```

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by bluestargazer on 2008-05-02
I'm brand new to ubunutu, i just installed 8.04 last night. i'm not tech savy and my friend was suppose to help. I need tips on how to get things sorted out like Wireless internet.

My toshiba satallite can't even detect any wireless networks, and i'm at my school library, so there is a network available. Any tips or if there is more info that i should give to make myself clear. i'm just a confused noob.

---

