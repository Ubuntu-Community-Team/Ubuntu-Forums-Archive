---
title: "[SOLVED] Wireless Connects, but host not found"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by weaverryan on 2008-06-20
Hey guys-

I'm a pretty experienced ubuntu user, but networking is not my forte. After connecting to my wireless network this morning (just like I do everyday), I failed to get internet. Everything is connecting just fine, but I'm getting an unknown host error (for example) when I ping.

Here's my question: If my /etc/resolv.conf file looks fine, why is my DNS screwed up?

In fact, everything looks just fine - I can't track down any problems. Here's some output:

```
cat /etc/resolv.conf
#
### END INFO

search hsd1.mi.comcast.net.


nameserver 68.87.77.130
nameserver 68.87.72.130
```

```

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BallsOnEvans"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:47:64:78   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=66/100  Signal level=-67 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```
iwconfig
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:6a:4b:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752m-v3.22 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:ad:b5:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.109 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0
```


I've tried restarting and messing with everything I know how. There were no kernel upgrades between today and yesterday, and no changes to my computer that I can recall except for 2 things
1. apt-get remove firestarter
2. I manually downloaded and installed the new virtualbox-ose-modules-generic package for my new kernel version (which was new a few days ago, but the wireless WAS working with it before today)

I need desperate help - I make a living on my computer!!!

Thanks!

---

### Post by weaverryan on 2008-06-20
I fixed it.

The problems WAS that I had uninstalled firestarter. I had noticed that firestarter was failing to start when the system was loading. So, I figured IS would just uninstall it if it wasn't even working. Bad choice. As soon as I reinstalled it, everything worked (without even needing a restart).

So, don't kill your firestarter

---

