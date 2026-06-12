---
title: "wireless card looses Internet access after about 5 min"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by jjf on 2007-07-31
I really hope someone can help me with this.  Based on an afternoon of Internet reserach, it seems to be a fairly common problem with Feisty.  

My wireless card (which worked fine in Dapper) connects without problem to my WEP-secured wireless network.  I can browse the Internet, etc, for about 5 minutes, then Internet access cuts out.  Pages I'm trying to view (in Firefox) get stuck with "Looking for google.com" in the status bar.  Eventually they time out.  Sometimes after 30-45 minutes of waiting, the connection automagically returns.

I don't lose access to my wireless network, just to the Internet.  The lights on my card stay lit.  Network-manager still tells me I'm connected.  I'm still able to ping my router.  But I'm not able to ping outside sites (say, google.com).

I thought maybe the problem was ndiswrapper, so I downloaded the trial version of software called Linuxant that's supposed to provide wrappers for Windows drivers.  Same problem.

I thought maybe it was my card.  I bought a new D-Link that works natively with Fiesty (using restricted drivers).  It had the same problem.

It's not my router -- my sister in law's MacBook has no trouble.

I booted into my windows partition, and found my original wireless card maintains its connection just fine there.

So the problem is Ubuntu's handling of wireless PCMCIA cards on my Thinkpad T23.  

Wireless access is crucial before I have to go back to school in September, so I really hope someone can help me.  Even just some diagnostics I might run or log files I might check to figure out what's going on would be appreciated.

Thanks.

---

### Post by kevdog on 2007-07-31
What card and drivers are you using??

lspci -nn
lshw -C network

---

### Post by jjf on 2007-07-31
I have a GigaFast (can't remember the model #), using the net8180 driver via the Linuxant software right now (though I had the same trouble with ndiswrapper and with a natively supported card).

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #2) [8086:2484] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #3) [8086:2487] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 41)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 01)
01:00.0 VGA compatible controller [0300]: S3 Inc. SuperSavage IX/C SDR [5333:8c2e] (rev 05)
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:02.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0449] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 41)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
```

sudo lshw -C network
```
  *-network               
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:aa:e2:e3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:c0200000-c0200fff ioport:6400-643f irq:11
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@03:00.0
       logical name: wlan0
       version: 20
       serial: 00:90:47:07:3c:d0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=driverloader driverversion=driverloader 2.38 - Linuxant Dr ip=192.168.0.106 latency=168 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11-DS
       resources: ioport:2000-20ff iomemory:c4000000-c40001ff irq:11
```

Thanks for looking!

---

### Post by noob12 on 2007-08-01
Can you please post the output of each of these commands
```

cat /etc/network/interfaces

iwconfig

iwlist scan

cat /etc/resolv.conf

```

*During one of your lost connectivity experiences*, can you please grab the output of these commands and save them, then post them when you regain connectivity
```

ifconfig -a

iwconfig

cat /etc/resolv.conf

```

---

