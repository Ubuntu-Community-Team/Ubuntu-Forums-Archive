---
title: "Can't connect to wireless."
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by ryan46 on 2014-01-29
Did a fresh installation of Ubuntu 12.04. Got it connected to Wifi. After doing the updates for the 12.04 version, I can't seem to connect to the wireless anymore. It still recognises that the wireless connections are there, but it just won't connect.. Any ideas?

EDIT: I'm running it on an Acer Aspire One D255E with the [COLOR=#000000][FONT=Arial]Broadcom BCM4313.[/FONT][/COLOR]

---

### Post by ryan46 on 2014-01-29
```
ryan@RyanUbuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:00:4e:0c:11:47  
          inet6 addr: fe80::9200:4eff:fe0c:1147/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:4035
          TX packets:114 errors:59 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8902 (8.9 KB)  TX bytes:26019 (26.0 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.2 KB)  TX bytes:5248 (5.2 KB)
```

```
ryan@RyanUbuntu:~$ sudo lshw -C network
[sudo] password for ryan: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 90:00:4e:0c:11:47
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:56000000-56003fff
```

```
ryan@RyanUbuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

