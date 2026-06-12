---
title: "Wired connection not working"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by fangorn2 on 2015-12-02
I am on a Toshiba Satellite L50-A-161 with Ubuntu 14.04 LTS.
I had no problem whatsoever with wi-fi connections so far, and never had the chance to test wired connections.
Now I need to use the cable, since the router I am using at present, an old D-Link DSL-2542B, does not have wi-fi.
I realised that I am unable to browse the Internet via cable with my Toshiba: Internet browsing works for 20s/half a minute, then stops.
I tried to restart the machine many times but Firefox works for 20s/half a minute as before then stops.
However if I ping -c3 my router or Google's DNS 8.8.8.8, the results are: 3 packets transmitted, 3 received, 0% packet loss
An old desktop pc running the same Ubuntu 14.04 LTS connects to the Internet through the same router with no problem whatsoever.

I tried to disable wi-fi, as suggested in [an old topic]("http://ubuntuforums.org/showthread.php?t=2239677"), with no results.
The result of command 'sudo lshw -C network', ran in my Toshiba laptop, is below:

```

fangorn@SATELLITE-L50-A-161:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 48:d2:24:7a:54:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.19.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:30 ioport:3000(size=256) memory:d3400000-d3403fff
  *-network
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 54:be:f7:27:f0:ef
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:32 memory:d1000000-d103ffff ioport:2000(size=128)


```

---

### Post by rslater on 2015-12-03
I am not sure if I am missing something here.  You appear to have an internet connection but your Browser stops after 20 seconds or so.  Are you claiming a browser problem or network problem?  Try ping 8.8.8.8 and leave it running, does the connection stay live for more than 30 seconds.  Have you tried Chrome or another browser?

Let us know how you get on...

---

### Post by fangorn2 on 2015-12-07
Thanks for your reply.
It was a simple dns issue. I only had my router as a dns server, so I simply added a pair of secure and public dns server addresses and now everything is ok.

---

