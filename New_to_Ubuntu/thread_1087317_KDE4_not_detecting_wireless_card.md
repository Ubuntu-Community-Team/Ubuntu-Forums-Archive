---
title: "KDE4 not detecting wireless card"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-03-04
I installed ubuntu with Gnome and then installed KDE4 nightly version later on so I can switch between sessions at the login screen. Gnome has no problem detecting my wireless card and connecting to the internet but whenever I use KDE4 I can't connect with either firefox or konqueror. When I use Gnome, I get an icon showing my signal strength but I don't get that with KDE4. Can someone help with this please?

Thanks a bunch

---

### Post by Crafty Kisses on 2009-03-04
What are the results of these commands?
```
sudo lshw -C network
lspci
```

---

### Post by anewguy on 2009-03-04
> **Sup3r3g0 said:**
> I installed ubuntu with Gnome and then installed KDE4 nightly version later on so I can switch between sessions at the login screen. Gnome has no problem detecting my wireless card and connecting to the internet but whenever I use KDE4 I can't connect with either firefox or konqueror. When I use Gnome, I get an icon showing my signal strength but I don't get that with KDE4. Can someone help with this please?

Thanks a bunch

do you have knetworkmanager installed?  If I understand things correctly, for kde4 you need knetworkmanager.  There are several posts for this on a yahoo search, but since I don't use kde4 I couldn't test this for you.  Some posts indicate a bug in what's included in 1 of the packages, but indicate the latest knetworkmanager in the repositories would fix it.

Dave :)

---

### Post by Sup3r3g0 on 2009-03-04
Here's what I got:
```
 *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:6b:7a:0f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:37:93:fa:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.107 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:3e:3f:ec:c8:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

I'll check if I have kdenetworkmanager

Thanks for all your help

---

### Post by Sup3r3g0 on 2009-03-04
Thanks. After installing kde network manager, I was able to connect.

---

