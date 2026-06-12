---
title: "ASUS F3S Laptop On-Board Network Not Working Under Dapper"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by android32 on 2007-08-20
I recently got an ASUS F3S model laptop with on-board networking. I'm currently dual-booting with Vista (I know, I know) and Dapper. On Dapper, my wireless works fine but no wired connection is found under the network manager. However, under Vista I found that my on-board network card is an Attansic L1 Gigabit ethernet. I found drivers for this on-board network card on sourceforge: [http://sourceforge.net/projects/atl1/](http://sourceforge.net/projects/atl1/)   .
However, whenever I try to so a **sudo make install** command, it fails and gives the following response 
```
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2250: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2260: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2271: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2272: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2273: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2275: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2276: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2277: error: dereferencing pointer to incomplete type
/home/android32/Desktop/atl1-2.0.7-linux-2.6.20/atl1_main.c:2278: error: dereferencing pointer to incomplete type

```
and so on and so forth.

I downloaded my linux kernel headers and yet this still doesn't work. Is there something obvious I'm missing?

By the way, my LSPCI is as follows:
```
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 2a00 (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 2a01 (rev 03)
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 03)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 03)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 03)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation: Unknown device 2841 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation: Unknown device 2843 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation: Unknown device 2845 (rev 03)
0000:00:1c.4 PCI bridge: Intel Corporation: Unknown device 2847 (rev 03)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 2849 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2815 (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation: Unknown device 2850 (rev 03)
0000:00:1f.2 0106: Intel Corporation: Unknown device 2829 (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71de
0000:02:00.0 Ethernet controller: Unknown device 1969:1048 (rev b0)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:04:00.0 0106: Unknown device 197b:2360 (rev 02)
0000:09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (rev 05)
0000:09:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0000:09:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 12)
0000:09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0000:09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by canceLinux on 2007-09-15
Now i'm starting to tell.. for feisty..

there's a few documents for this on the internet..

[http://asus-linux.blogspot.com](http://asus-linux.blogspot.com)

---

