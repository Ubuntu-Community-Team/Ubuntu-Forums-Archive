---
title: "Lost all connection after removing network-manager with Xubuntu 16.04"
date: 2017-12-06
forum: Networking &amp; Wireless
---

### Post by ozanoz on 2017-12-06
Hello everyone, 

I am having some difficulties in configuring my network. I am new to Linux and currently using Xubuntu 16.04, trying to establish a wired connection.
I am trying to connect to the internet from a dorm in which connections are allocated centrally through a router (I believe), and so I have registered my mac address and need to configure my connection with a certain ip address and so on. 
Not surprisingly, I wasn't able to do it and while I was following some instructions that I have found here, I have removed the network-manager and completely lost track of what I am doing. 
I am posting my latest outputs here for your observation.
 Thank you very much in advance for your time and help. 

p.s. I won't be able to answer your messages for some time since it is way past bedtime here!

my /etc/network/interfaces looks like
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
 2
 3
 4
 5
 6
 7
 8
 9
10
[/TD]
[TD="class: code"][COLOR=#000000]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto enp1s0f2
iface enp1s0f2 inet static
address 144.122.124.30
netmask 255.255.255.0
broadcast 144.122.124.255
gateway 144.122.124.1
dns-nameservers 144.122.199.90 144.122.199.93[/COLOR]
[/TD]
[/TR]
[/TABLE]

ifconfig
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
[/TD]
[TD="class: code"][COLOR=#000000]enp1s0f2 Link encap:Ethernet HWaddr 
 inet addr:144.122.124.30 Bcast:144.122.124.255 Mask:255.255.255.0
 UP BROADCAST MULTICAST MTU:1500 Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:65536 Metric:1
 RX packets:539 errors:0 dropped:0 overruns:0 frame:0
 TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:46218 (46.2 KB) TX bytes:46218 (46.2 KB)

wlp2s0 Link encap:Ethernet HWaddr 
 inet addr:192.168.43.225 Bcast:192.168.43.255 Mask:255.255.255.0
 inet6 addr: fe80::f203:8cff:feec:d123/64 Scope:Link
 UP BROADCAST MULTICAST MTU:1500 Metric:1
 RX packets:136 errors:0 dropped:0 overruns:0 frame:0
 TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:14232 (14.2 KB) TX bytes:19687 (19.6 KB)[/COLOR]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
[/TD]
[TD="class: code"][COLOR=#000000]ozzy@ozan-E402NA:~$ sudo lshw -C network
 *-network
 description: Ethernet interface
 product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 0.2
 bus info: pci@0000:01:00.2
 logical name: enp1s0f2
 version: 06
 serial: 
 size: 10Mbit/s
 capacity: 100Mbit/s
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt
10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI
duplex=half firmware=rtl8402-1_0.0.1 10/26/11 ip=144.122.124.30 latency=0 link=no
multicast=yes port=MII speed=10Mbit/s
 resources: irq:372 ioport:e000(size=256) memory:91214000-91214fff memory:91210000-
91213fff
 *-network
 description: Wireless interface
 product: QCA9565 / AR9565 Wireless Network Adapter
 vendor: Qualcomm Atheros
 physical id: 0
 bus info: pci@0000:02:00.0
 logical name: wlp2s0
 version: 01
 serial: 
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
 configuration: broadcast=yes driver=ath9k driverversion=4.10.0-38-generic firmware=N/A
ip=192.168.43.225 latency=0 link=no multicast=yes wireless=IEEE 802.11
 resources: irq:23 memory:91100000-9117ffff memory:91180000-9118ffff[/COLOR]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3
4
5
6
[/TD]
[TD="class: code"][COLOR=#000000]ozzy@ozan-E402NA:~$ dmesg | grep r8169
[ 2.362038] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 2.363020] r8169 0000:01:00.2 eth0: RTL8402 at 0xffffbd4dc06b9000,, XID
04000800 IRQ 372
[ 2.429298] r8169 0000:01:00.2 enp1s0f2: renamed from eth0
[ 6.577285] r8169 0000:01:00.2 enp1s0f2: link down[/COLOR]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3
4
5
6
7
[/TD]
[TD="class: code"][COLOR=#000000]ozzy@ozan-E402NA:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 144.122.124.1 0.0.0.0 UG 0 0 0 enp1s0f2
144.122.124.0 0.0.0.0 255.255.255.0 U 0 0 0 enp1s0f2
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 enp1s0f2
192.168.43.0 0.0.0.0 255.255.255.0 U 0 0 0 wlp2s0[/COLOR]
[/TD]
[/TR]
[/TABLE]


I can't figure this out myself, need your help..
Have a nice day/night
Ozan

---

### Post by ozanoz on 2017-12-07
Nobody?

---

### Post by kurt18947 on 2017-12-07
I know that it is possible to configure a network connection manually. I'm not much help with how to do it. I have learned to be cautious about using advice found by random googling. The trick is to determine which sources are credible and which are likely to result in a reinstall. In your position I might work with a live USB without persistence enabled. Leave Network Manager enabled and try to connect changing settings as required within Network Manager. That way if things get crossways a reboot gets you back to default settings. Sorry I'm not more help.

---

### Post by ozanoz on 2017-12-07
Thanks for the reply. I will do as you suggest, it seems like a better idea to stick with the network manager. 
I am sure the source is credible enough, at least he had a rationale to his every step but I am afraid my knowledge wasn't up for it .

---

