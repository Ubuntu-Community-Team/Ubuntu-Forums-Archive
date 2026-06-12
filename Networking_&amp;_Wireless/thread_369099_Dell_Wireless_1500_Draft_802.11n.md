---
title: "Dell Wireless 1500 Draft 802.11n"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Ek0nomik on 2007-02-24
I need some help getting my wireless Internet to work on this laptop.  I have been searching the forums all night trying to get this issue solved, but I haven't had any luck.

Currently, I believe I have yet for Ubuntu to even recognize my wireless device.  I have the Network Manager working, and I only have a Wired connection listed.

Here are some results of commands:

```
fleur@fleur-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

```
fleur@fleur-laptop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

```
fleur@fleur-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:4F:DA:9C  
          inet addr:137.28.247.42  Bcast:137.28.247.255  Mask:255.255.254.0
          inet6 addr: fe80::219:b9ff:fe4f:da9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3903347 (3.7 MiB)  TX bytes:381084 (372.1 KiB)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

```
fleur@fleur-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

```

If I goto System/Administration/Networking, my only options are Wired and Modem connection.

If I go to my Network Connection in the upper right hand corner, I have eth0 and lo.  eth0 switched between sending/receiving & idle.  lo doesn't seem to do anything.  Could someone clarify what lo and eth0 actually mean?

I'd appreciate any help!  I know the card works, because I got it running in Windows.  I want to try to get Ubuntu the wireless Internet working so I can take my laptop to lectures starting Monday.  Thanks!

---

### Post by Ek0nomik on 2007-02-24
I still haven't had any luck, even after following the ndiswrapper and driver directions.

Any ideas?

---

### Post by Ek0nomik on 2007-02-24
```
fleur@fleur-laptop:~$ lspci | grep Broadcom\ Corporation
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

My wireless card is thee, I just need Ubuntu to recognize it.

I have followed guide after guide, I just can't seem to get it running.

---

### Post by Ek0nomik on 2007-02-25
Does anyone have any ideas by any chance?

---

### Post by Ek0nomik on 2007-02-28
**If, while searching the Ubuntu Forums, you come across this thread hoping for a solution, I found one.**

[http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)

---

