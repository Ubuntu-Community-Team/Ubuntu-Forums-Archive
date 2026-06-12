---
title: "Dell wireless card problem (worked in 7.04 and 7.10)"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by victorjake on 2008-10-22
Okay, so I installed 7.04 first and followed the guide (I googled 'dell wireless ubuntu' and followed the first guide) in order to install the wireless for my dell. It worked (it could see the networks around). Upgraded to 7.10. It worked. Upgraded to 8.04 and it does not work. I could not see the networks around and when I manually configured it, it keeps asking me for the network key even though I keep inputting the right key.

Please help, I just got into linux about a week ago and I finally had time to upgrade (from 7.04) today and found out that my settings do not transfer to 8.04.

Here is lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Here is ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:14:22:a6:da:90  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fea6:da90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3075543 (2.9 MB)  TX bytes:282899 (276.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:159100 (155.3 KB)  TX bytes:159100 (155.3 KB)

---

### Post by Ayuthia on 2008-10-22
There is a new wireless module that replaces the bcm43xx that was used in prior versions of Ubuntu.  It was introduced in the 2.6.24 kernel (used in 8.04).  If you want to use it, just go into the Terminal and install (if you have a working wired connection):
```
sudo apt-get install b43-fwcutter
```It will ask you if you want it to find the firmware for you.  Select yes and it should install it for you.

Just as a note, you do have a Broadcom wired ethernet card (02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)).  This means that it uses the b44 dmodule.  The new b43 (the one that replaces the bcm43xx) and b44 moodules also use the ssb module.  Because of this, there are additional steps that you will need to do if you want to use ndiswrapper or the new wl module.  If you want to use ndiswrapper, please use this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It gives you the workaround for ndiswrapper.

My recommendation is to install b43 first and see if you like it.  If it is fine then you are set, but if you don't like it, then try either the wl or ndiswrapper option.  The b43 module does not require any additional work after you install the missing firmware.

Hope that helps.

---

### Post by victorjake on 2008-10-22
it worked! thank you very much.

---

