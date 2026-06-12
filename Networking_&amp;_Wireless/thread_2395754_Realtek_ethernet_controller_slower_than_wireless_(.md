---
title: "Realtek ethernet controller slower than wireless (also slow) - Ubuntu 16.04"
date: 2018-07-06
forum: Networking &amp; Wireless
---

### Post by kkalanda on 2018-07-06
Hi all,


I've decided to dig into why my home server has performed so poorly at streaming media content to the rest of my network. Internet connection has been very slow relative to my Windows machine.


```
[kalanda@home] ~> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial
```


```
[kalanda@home] ~> sudo lshw -C network
[sudo] password for kalanda:
  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 4c:bb:58:1b:4e:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=4.4.0-98-generic firmware=N/A ip=192.168.2.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:93 ioport:e000(size=256) memory:d0700000-d0703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: enp2s0f2
       version: 0a
       serial: 80:ee:73:a6:ac:e9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.2.22 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:89 ioport:d000(size=256) memory:d0614000-d0614fff memory:d0610000-d0613fff
```


```
[kalanda@home] ~> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlp1s0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp1s0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s0f2
```


```
[kalanda@home] ~> curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
Retrieving speedtest.net configuration...
Testing from Bell Canada (69.157.37.40)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by TELUS (Toronto, ON) [0.94 km]: 6.82 ms
Testing download speed................................................................................
Download: 21.49 Mbit/s
Testing upload speed................................................................................................
Upload: 28.72 Mbit/s
```


```
[kalanda@home] ~> ifconfig
enp2s0f2  Link encap:Ethernet  HWaddr 80:ee:73:a6:ac:e9
          inet addr:192.168.2.22  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3228775 (3.2 MB)  TX bytes:677730 (677.7 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:286290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:221243907 (221.2 MB)  TX bytes:221243907 (221.2 MB)


wlp1s0    Link encap:Ethernet  HWaddr 4c:bb:58:1b:4e:98
          inet addr:192.168.2.26  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34290893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29874521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50600021842 (50.6 GB)  TX bytes:3213435681 (3.2 GB)
```


```
[kalanda@home] ~> vnstat


                      rx      /      tx      /     total    /   estimated
 enp2s0f2:
       Jul '18     51.16 MiB  /    1.99 MiB  /   53.15 MiB  /  297.00 MiB
     yesterday     49.17 MiB  /    1.53 MiB  /   50.70 MiB
         today      1.99 MiB  /     465 KiB  /    2.45 MiB  /      --




 wlp1s0:
       Jul '18     47.89 GiB  /    3.26 GiB  /   51.14 GiB  /  293.26 GiB
     yesterday     25.86 GiB  /    1.86 GiB  /   27.72 GiB
         today     22.03 GiB  /    1.39 GiB  /   23.42 GiB  /   57.75 GiB
```


I tried disabling my wireless connection with


```
sudo ifconfig wlp1s0 down
```


but then my network transfer speeds dropped to the KB/s and my server couldn't establish an internet connection. When I plugged the ethernet cable into my laptop instead and went to speedtest.net, I was able to get download speed of 269.05Mbps and 322.37Mbps upload, so it's not the cable. Does anyone have an idea of what's going on here? I'm thinking of just buying a new network card. Thanks!

---

### Post by TheFu on 2018-07-06
TL;DR.

Don't put 2 NICs on the same subnet.  Either use wifi or use wired. Don't use both.

NEVER download code/scripts/programs and directly run them on the computer.   If you see **curl {URL}| bash - **RUN!

---

### Post by kkalanda on 2018-07-06
Originally I just had WiFi and couldn't transfer faster than 4MB/s. Could it be that my card is not using 802.11n? I also tried hooking up ethernet/disabling WiFi and as I mentioned, it was incredibly slow.

I appreciate the concern about running the github code. Do you have a suggestion on how to better test internet speed from CLI?

---

### Post by TheFu on 2018-07-06
Disable wifi.  Only use wired.  Check all network settings, especially the route and DNS.
The 1st post above shows wired and wifi on the same subnet.  The wifi is preferred since the default gateway is tied to it when the default should always be wired. Always.

To test network performance, I use iperf3 between systems I own.  To test internet performance, I use speedtest-cli. My comment is about running code from random websites that aren't vetted or cryptographically signed.

---

### Post by kkalanda on 2018-07-06
I could be wrong, but I think the github code I ran is effectively the source code for the speedtest-cli tool.

Anyway, I actually ended up speeding up my performance by updating my drivers as per [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-The-rtlwifi_new-driver-from-lwfinger](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-The-rtlwifi_new-driver-from-lwfinger)

Oddly enough, I'd done it before and noticed no difference. The second time seemed to do the trick. Now I'm getting downloads and uploads in the 200-300Mbit/s

Thanks for the responses :)

---

