---
title: "Realtek 8111G not using all speed after installing driver"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by markus33 on 2016-02-06
Hello,
I installed the Realtek driver and it made my connection faster, but it is still slower. If i could get help with this it would be awesome so i wouldn't have to go back to Windows or order a external Ethernet to USB adapter.
And i use a Ethernet cable. The network card is a Realtek 8111G and the mobo is a MSI H81M-E33-V2.

Thanks,
Markus

---

### Post by TheFu on 2016-02-06
Welcome to the forums.  This is a common issue for Realtek GigE cards.

Run **sudo lshw -C network** to see which driver is being used. Then you can search the forums for the exact chip, model and driver to find a solution.  Hopefully, it doesn't require getting source code and compiling a driver for it.

I've been lucky, all the realtek network adapters I have here sorta "just work", but when purchasing an addon NIC, I always get an Intel PRO/1000 to avoid all these issues. They are only $25 and the e1000 driver is THE INDUSTRY STANDARD.

Here's an example:
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: fc:aa:14:a7:06:51
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=172.22.22.20 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:e000(size=256) memory:f7e00000-f7e00fff memory:f0000000-f0003fff
```

See how the r8169 is used and notices the product and version parts above?  
**RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller** and version **0c**.  That version is important.  The machine this NIC is inside is a Pentium G3258, not especially powerful (but a tremendous value for a $60 CPU). It is an NFS server, Plex server, Calibre server and probably a few other things that I've forgotten. It was doing whatever it normally does.  The hostname and network name is "istar."

Also, it would be smart to test the throughput before and after any change. Use **iperf** for this.  It removes a slow disk from the bandwidth estimates.

So, I connected from a few different clients to that realtek machine (istar):
a)```

$ iperf -c istar
------------------------------------------------------------
Client connecting to istar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.13 port 37470 connected with 172.22.22.20 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   656 MBytes   550 Mbits/sec
```
Not great. This is from a chroot ubuntu under ChromeOS.  It is using a USB3-GigE wired ethernet going through 2 GigE switches.  I've tested everything with a different laptop and another chromebook booting Ubuntu directly and saw 900+Mbps. So, the issue is this chromebook and/or chromeos and/or the chroot. In theory, this chromebook has double the RAM and a CPU that is over 2x faster than the old chromebook.  Reran the test a few times - saw 155Mbps and 687Mbps results.  Not used to seeing such wildly different results.

b) ```
$ iperf -c istar
------------------------------------------------------------
Client connecting to istar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.6 port 53416 connected with 172.22.22.20 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.10 GBytes   943 Mbits/sec
```
This is from a Core i7 mini-desktop. Much better - this is what I expected.

I was on a roll ... from a raspberry Pi v2 (running Kodi at the time), 
c) ```
$ iperf -c istar
------------------------------------------------------------
Client connecting to istar, TCP port 5001
TCP window size: 43.8 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.28 port 36328 connected with 172.22.22.20 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   112 MBytes  93.7 Mbits/sec
``` 
Well, that makes complete sense - the raspberry pi only has a 100 Mbps network port. Getting 93Mbps from it is actually pretty impressive - it was playing a hidef movie at the time, streamed from istar too, BTW.

Anyway - hope this all helps.  And thanks for having me see that this chromebook's network has an issue. ;(

---

