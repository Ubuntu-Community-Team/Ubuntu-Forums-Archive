---
title: "Lenovo Z50-70 WiFi connection not working.. sort of? Kubuntu 16.04"
date: 2016-09-29
forum: Networking &amp; Wireless
---

### Post by SnazzleLabsYT on 2016-09-29
I'm running the latest Kubuntu 16.04.1 on my Lenovo Z50-70, and the WiFi isn't playing nice. Most of the time, I stay connected for 5 minutes, and then it stops working, totally. From the Live USB I have, it works, but after 2 hours, I have to disconnect and reconnect the WiFi. On the actual install, disconnecting and reconnecting doesn't help. I have 3 different WiFi networks to pick from - separate bands from my provider's router and a dual band AirPort Extreme. Neither of them work. I know this isn't due to WiFi problems - at the same time of my laptop not working, my phone works absolutely fine. Can someone please help?

---

### Post by Bucky Ball on 2016-09-29
Perhaps. Please post the output of the following two commands between code tags to start with.

```
sudo lshw -C network
iwconfig
```

---

### Post by SnazzleLabsYT on 2016-09-29
Here's the first command;
```
[FONT=monospace][COLOR=#000000]*-network                [/COLOR]
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 68:f7:28:0f:e1:57
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp
 mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-
NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port
=MII speed=10Mbit/s
       resources: irq:45 ioport:5000(size=256) memory:c3504000-c3504fff memory:c3500000-
c3503fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: c0:38:96:12:af:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-38-generic firm
ware=N/A ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:4000(size=256) memory:c3400000-c3403fff

[/FONT]
```

and the second..

```
[FONT=monospace][COLOR=#000000]lo        no wireless extensions.[/COLOR]

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"VM818866-2G"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 50:6A:03:4B:BE:28    
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm    
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0
[/FONT]
```

---

### Post by SnazzleLabsYT on 2016-10-01
Anyone?

---

### Post by jeremy31 on 2016-10-01
First thing to try is ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Then reboot and test

---

