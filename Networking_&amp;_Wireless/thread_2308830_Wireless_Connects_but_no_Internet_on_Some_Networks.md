---
title: "Wireless Connects but no Internet on Some Networks(Unknown Host)"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by Johannes_Kolsky on 2016-01-06
So much thanks to anyone who can help me on this. This problem has been hounding me for two weeks. My NB205 Netbook, running Ubuntu 15.04 (previously 13.04), readily connects to wireless and wired networks, but whether I get internet depends on the network. At my house and the library (wireless and wired), I get an "unknown host" reply on my pings. At my parents' house and work, I get internet fine, no hitches. Other people at my house can access the internet, and obvious people at the library can.

The issue started with infrequent (once a week), sudden no-internet episodes on my home network, which I solved by turning the wireless interface wlan0 off and on again and turning networking and wi-fi off and on from the Network Manager menu. Then one day I had no internet access and nothing I did could get it back. I've tried reinstalling Network Manager, setting up the connection manually with /etc/network/interfaces, reinstalling resolv.conf, changing the DNS servers in Network Manager, restarting Network Manager and networking, doing a /etc/init.d/dns-clean, and the latest, upgrading my entire system from 12.04 to 14.04. No changes. ](*,)

Wireless card driver is ath9k. I've had issues with it before, which were solved by updating/changing the driver.

Info: I did these at my parents' house where the internet DOES work, so not sure how useful they are.

output of ifconfig: (teredo is new since 2 days ago, problem existed before then)
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:fe:02:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:31746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2425307 (2.4 MB)  TX bytes:2425307 (2.4 MB)


teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 00:24:d2:96:f7:c5  
          inet addr:10.202.46.6  Bcast:10.202.46.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d2ff:fe96:f7c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22613959 (22.6 MB)  TX bytes:8562287 (8.5 MB)

```
output of iwconfig:

```

wlan0     IEEE 802.11bgn  ESSID:"Einstein"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F8:8E:85:BF:53:F3   
          Bit Rate=52 Mb/s   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:186   Missed beacon:0


lo        no wireless extensions.


teredo    no wireless extensions.


eth0      no wireless extensions.

```

output of lshw -c network:
```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:96:f7:c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-42-generic firmware=N/A ip=10.202.46.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:fe:02:01
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:40600000-4061ffff

```

---

