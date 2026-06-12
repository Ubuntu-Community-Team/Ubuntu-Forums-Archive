---
title: "Ethernet speed is slowing down after some hours"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by daybat on 2013-10-02
hello!

I have ubuntu installed on my home server. Server has 2 ethernet cards 1G each & one Wi-Fi card. One ethernet card (eth0) & one Wi-Fi (wlan0) are in bridge (br0) and work in my inner network. The other ethernet card (eth1) is connected to the Internet via PPPoE (ppp1). After some period of time my Internet speed becomes very slow: from 20Mbps to 4-5Mbps. After resetting my eth1 card:
# poff
# ifconfig eth1 down
# ifconfig eth1 up
# pon provider
after this the speed becomes 20Mbps for next some hours.

Normal speed:
[IMG]http://www.speedtest.net/result/3006350609.png[/IMG]

Slow speed:
[IMG]http://www.speedtest.net/result/3006299553.png[/IMG]

What can be the problem?

```
**root@mice:~# lshw -C network**
  *-network               
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: cc:b2:55:00:61:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-54-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f7400000-f741ffff memory:f7420000-f742ffff
  *-network
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 10
       serial: c8:d3:a3:83:d6:20
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.1 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d000(size=256) memory:f7321000-f73210ff memory:f7300000-f731ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 06
       serial: 54:04:a6:94:fa:3f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:53 ioport:b000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff


**root@mice:~# ethtool -i eth1**
driver: r8169
version: 2.3LK-NAPI
firmware-version: N/A
bus-info: 0000:06:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes


**root@mice:~# ethtool -i eth0**
driver: r8169
version: 2.3LK-NAPI
firmware-version: rtl_nic/rtl8168e-2.fw
bus-info: 0000:08:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes


**root@mice:~# ifconfig**
br0       Link encap:Ethernet  HWaddr 54:04:a6:94:fa:3f  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131967169 errors:0 dropped:211 overruns:0 frame:0
          TX packets:63473281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10000 
          RX bytes:185459472130 (185.4 GB)  TX bytes:34104821610 (34.1 GB)

eth0      Link encap:Ethernet  HWaddr 54:04:a6:94:fa:3f  
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:133960713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56609422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10000 
          RX bytes:187446611584 (187.4 GB)  TX bytes:23974991524 (23.9 GB)
          Interrupt:53 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr c8:d3:a3:83:d6:20  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25960534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13998750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10000 
          RX bytes:32984242119 (32.9 GB)  TX bytes:5697859955 (5.6 GB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:604772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49406397 (49.4 MB)  TX bytes:49406397 (49.4 MB)

mon.wlan0 Link encap:UNSPEC  HWaddr CC-B2-55-00-61-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2645146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:441084358 (441.0 MB)  TX bytes:0 (0.0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:77.51.122.145  P-t-P:77.51.191.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3452429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2626751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3668772395 (3.6 GB)  TX bytes:1991838011 (1.9 GB)

wlan0     Link encap:Ethernet  HWaddr cc:b2:55:00:61:e7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2252253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6878467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10000 
          RX bytes:130932879 (130.9 MB)  TX bytes:10268554923 (10.2 GB)



**root@mice:~# cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto domolink
iface domolink inet ppp
pre-up /sbin/ifconfig eth1 up
provider domolink
post-up /etc/cgi-bin/iptables.rules.sh
post-up /sbin/ifconfig ppp1 txqueuelen 10000

auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255


auto br0
iface br0 inet static
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
bridge-ports eth0 wlan0
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
dns-search intranet
post-up /etc/cgi-bin/post-up.sh


**root@mice:~# cat /etc/cgi-bin/post-up.sh**
#!/bin/sh
/sbin/ethtool -s eth0 speed 1000 duplex full wol d
/sbin/ethtool -s eth1 speed 100 duplex full wol d

/sbin/ifconfig eth0 mtu 9000

/sbin/ifconfig eth0 txqueuelen 10000
/sbin/ifconfig eth1 txqueuelen 10000
/sbin/ifconfig wlan0 txqueuelen 10000
/sbin/ifconfig br0 txqueuelen 10000


echo 4096 > /proc/sys/net/netfilter/nf_conntrack_expect_max
echo 2 > /proc/sys/net/ipv4/conf/all/arp_ignore
echo 1 > /proc/sys/net/ipv4/conf/all/arp_announce
echo 2048  > /proc/sys/net/ipv4/neigh/default/gc_thresh1
echo 8192  > /proc/sys/net/ipv4/neigh/default/gc_thresh2
echo 16384 > /proc/sys/net/ipv4/neigh/default/gc_thresh3
echo 300   > /proc/sys/net/ipv4/neigh/default/base_reachable_time

service dnsmasq restart
#service smbd restart
service netatalk stop
service netatalk start

ip route add blackhole 192.168.0.0/16
ip route add blackhole 172.16.0.0/12
ip route add blackhole 10.0.0.0/8

route add -net 224.0.0.0/4 dev ppp1
exit 0

**root@mice:~# uname -a**
Linux mice 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

