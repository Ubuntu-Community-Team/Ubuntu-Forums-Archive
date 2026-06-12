---
title: "Wired connection is not working | Xubuntu 16.04.3 lts"
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by ozanoz on 2017-12-07
Hello everyone, I am new to Linux and currently using xubuntu 16.04.3 with some asus laptop. 

I am trying to connect to the internet through a router in my dorm room. Wi-fi works without a fuss however I couldn't manage to get wired connection to work. 
I guess I am supposed to configure my network with an address, mask and gateway given to me from the university. I did so, both through network-manager's "edit connection" tab and through /etc/network/interfaces to no avail. 
I even deleted network manager and tried to set up my network from scratch (it was a complete failure, at least with nm I've got my wi fi working). 

I have a Realtek RTL8101 Ethernet controller with the latest drivers installed. 
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
16[/TD]
[TD="class: code"][COLOR=#000000]  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:01:00.2
       logical name: enp1s0f2
       version: 06
       serial: 
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.032.04-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:282 ioport:e000(size=256) memory:91214000-91214fff memory:91210000-91213fff[/COLOR][/TD]
[/TR]
[/TABLE]
and here are some other identifications[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3
4
5[/TD]
[TD="class: code"][COLOR=#000000]ozzy@ozan-E402NA:~$ nmcli device
DEVICE    TYPE      STATE        CONNECTION 
wlp2s0    wifi      connected    Ozanoz     
enp1s0f2  ethernet  unavailable  --         
lo        loopback  unmanaged    --   [/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Verdana]ozzy@ozan-E402NA:~$ dmesg | grep enp1s0f2
[    2.453500] r8101 0000:01:00.2 enp1s0f2: renamed from eth0
[    7.072185] IPv6: ADDRCONF(NETDEV_UP): enp1s0f2: link is not ready
[    7.072589] enp1s0f2: 0xffffad7dc06a9000, 10:7b:3c:8f:3c:8f, IRQ 282
[    7.196282] IPv6: ADDRCONF(NETDEV_UP): enp1s0f2: link is not ready
[/FONT][/COLOR]

and lastly ifconfig

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
25[/TD]
[TD="class: code"][COLOR=#000000]enp1s0f2  Link encap:Ethernet  HWaddr 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48025 (48.0 KB)  TX bytes:48025 (48.0 KB)

wlp2s0    Link encap:Ethernet  HWaddr  
          inet addr:192.168.43.225  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::f90a:83a2:8b5b:65f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4259264 (4.2 MB)  TX bytes:1498181 (1.4 MB)[/COLOR][/TD]
[/TR]
[/TABLE]
Well, I am completely lost and couldn't figure out a possible solution and need your help.
Have a good day/night.
Ozan

p.s. I am going to sleep now, and I won't be able to reply to your messages for some time. Hopefuly, see you tomorrow...

---

