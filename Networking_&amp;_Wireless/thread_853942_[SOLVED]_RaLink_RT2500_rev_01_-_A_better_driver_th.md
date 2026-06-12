---
title: "[SOLVED] RaLink RT2500 rev 01 - A better driver than kernel?"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by crjackson on 2008-07-09
I just installed 8.04 on the kids system.  My only complaint is that the kernel wireless driver yields a very slow connection.  This leads to online games running slow and complaints.

Is there a way to get full speed out of this wireless card or should I buy a new one?  If so, which one will give full 54g performance out of the box?

```
charles@charles-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
charles@charles-desktop:~$
```

---

### Post by jmtdstoc on 2008-07-09
I have an Asus WL-107G PCCARD with the RT2500 chip and it works out-of-the-box with Ubuntu 8.04, with perfect stability and performance.
I had some problems with it before because I had a hidden SSID on my access point... after making it visible everything worked perfectly.

Hope this helps you in any way!

---

### Post by comandrei on 2008-07-09
Check you speed (right click on the connection and choose Connection information). If it says anything less than 54Mb/s, open up /etc/rc.local (as root) and add the following lines:
```

   ifconfig wlan0 up
   iwconfig wlan0 rate 54M

```
Replace wlan0 with you interface name. Worked for me.

---

### Post by crjackson on 2008-07-09
> **comandrei said:**
> Check you speed (right click on the connection and choose Connection information). If it says anything less than 54Mb/s, open up /etc/rc.local (as root) and add the following lines:
```

   ifconfig wlan0 up
   iwconfig wlan0 rate 54M

```
Replace wlan0 with you interface name. Worked for me.

It does.  It says 1Mb/s and that just doesn't work too well.  I'm headed in for work right now, but I will try your suggestions when I get home tonight.

---

### Post by crjackson on 2008-07-09
> **jmtdstoc said:**
> I have an Asus WL-107G PCCARD with the RT2500 chip and it works out-of-the-box with Ubuntu 8.04, with perfect stability and performance.
I had some problems with it before because I had a hidden SSID on my access point... after making it visible everything worked perfectly.

Hope this helps you in any way!

Mine works out of the box too, but only at 1 Mb/s which doesn't cut it around here.

---

### Post by jmtdstoc on 2008-07-09
After reading "comandrei"'s post I checked my connection speed and it was only 6Mb/s!!!
I edited the file as he explained and now I get the full 54Mb/s.
The strange part is I never really noticed slow speeds.

---

### Post by crjackson on 2008-07-09
> **comandrei said:**
> Check you speed (right click on the connection and choose Connection information). If it says anything less than 54Mb/s, open up /etc/rc.local (as root) and add the following lines:
```

   ifconfig wlan0 up
   iwconfig wlan0 rate 54M

```
Replace wlan0 with you interface name. Worked for me.

Thanks, that did the trick.  I guess I won't be buying that new WiFi card after all :)

---

### Post by Feenix3k on 2008-07-13
I know sudo makes me root, but how do I open up /etc/rc.local  ?

---

### Post by crjackson on 2008-07-13
> **Feenix3k said:**
> I know sudo makes me root, but how do I open up /etc/rc.local  ?
```
gksudo gedit /etc/rc.local
```

---

### Post by Feenix3k on 2008-07-13
I see what I did wrong I had   iwconfig wlan0 rate 54m instead of     iwconfig wlan0 rate 54M

---

### Post by erans on 2008-07-14
Ahh! I'm having the same problem!

But I don't know which interface I'm using! :( How do I check? This has been driving me NUTS!!

EDIT: Nevermind, I see that it's listed under Connection Information. I edited my file and didn't see an increase from 1mbps to 54 in connection information, but I'll try restarting.

---

### Post by Feenix3k on 2008-07-14
> **comandrei said:**
> Check you speed (right click on the connection and choose Connection information). If it says anything less than 54Mb/s, open up /etc/rc.local (as root) and add the following lines:
```

   ifconfig wlan0 up
   iwconfig wlan0 rate 54M

```
Replace wlan0 with you interface name. Worked for me.

My roommate who is a geek says this locks wireless to the 54M rate. If you are at a place that does b or 11M it may not work. Unless the rate is reset to 11M.

---

### Post by erans on 2008-07-14
Damn, this didn't fix my problem. My speed is now listed at 54mbps, but whenever I start downloading, my ping to the router ranges from 200-500ms. A REALLY frustrating problem, and I'm having a ton of trouble installing the drivers from RaLink's site.

---

### Post by Feenix3k on 2008-07-14
I have thr Ralink drivers from a cd that came with my card, I just dont know how to use ndiswrapper to get them installed. Ubuntu 8.04 uses the rt2500pci driver which sets the system to 11M max.

---

### Post by Bert Mariën on 2008-08-20
> **comandrei said:**
> Check you speed (right click on the connection and choose Connection information). If it says anything less than 54Mb/s, open up /etc/rc.local (as root) and add the following lines:
```

   ifconfig wlan0 up
   iwconfig wlan0 rate 54M

```
Replace wlan0 with you interface name. Worked for me.

Worked for me as well.
I did at "fixed" after 54M (iwconfig wlan0 rate 54M fixed)

Thanks.

---

