---
title: "Lubuntu 20.04 LTS - network drops requiring restart on both wifi and ethernet"
date: 2021-07-27
forum: Networking &amp; Wireless
---

### Post by steve234 on 2021-07-27
Afternoon,

Since my 20.04 install my networking will disconnect, seemingly randomly, and not reconnect without a restart of the PC:


[LIST=1]
[*]This happens regardless of whether I use use a wifi or ethernet connection;
[*]Restarting the service does not seem to remedy the issue (e.g save me from having to restart); and
[*]Changing the wifi powersave to 2 (from 3) has not helped.
[/LIST]

It appears this PC is using Realtek ethernet and wifi devices:

```

sudo lshw -class network

*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 40:61:86:7b:00:28
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-63-generic duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=[NOT MY REAL LOCAL IP] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:fbfe0000-fbffffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4.2
       logical name: wlx1c4bd6472d61
       serial: 1c:4b:d6:47:2d:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u driverversion=5.8.0-63-generic ip=[NOT MY REAL LOCAL IP] multicast=yes wireless=IEEE 802.11bg


```


Any help diagnosing / things to try next time it randomly goes down would be greatly appreciated.

---

### Post by linerman on 2021-07-28
Hi,

I had a similar issue with that ethernet card. 
After[ installation of r8168 driver]("https://ubuntuforums.org/showthread.php?t=2456227&p=14012451#post14012451") and blacklisting system one, the card started to behave quite decent.

---

### Post by steve234 on 2021-08-08
Thanks, I must say I'm a little afraid of that without further diagnosis (see error logs below). I wonder if this is an IPv6 issue?

I've found that if I am on wired, I can toggle networking and get it back up. Dmesg for the drop / restart says:

```
[ 2160.566860] perf: interrupt took too long (4223 > 3977), lowering kernel.perf_event_max_sample_rate to 47250
[ 2643.701820] r8169 0000:02:00.0 enp2s0: Link is Down
[ 2646.474707] RTL8211B Gigabit Ethernet r8169-200:00: attached PHY driver (mii_bus:phy_addr=r8169-200:00, irq=IGNORE)
[ 2646.643550] r8169 0000:02:00.0 enp2s0: Link is Down
[ 2648.082268] r8169 0000:02:00.0 enp2s0: Link is Up - 100Mbps/Full - flow control rx/tx
[ 2648.082284] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


```

---

### Post by linerman on 2021-08-12
I got Realtek 8168 NIC and Asus Broadcom wifi card. 
I have IP4 and IP6 work on both of them. Never have a problem with these cards using default settings, nor switching between them.
The only problems I had with Realtek card were connected to r8169 driver. Although I've tried different kernels and different firmware version, the card was sometimes more stable (depends on kernel/firmware/), sometimes not.
If you dig deeper through the net or this forum, you would find a lot of issues with that NIC.
When I got rid of the r8169 driver, the unusual and random misbehavior of my ethernet connection had stopped.

---

