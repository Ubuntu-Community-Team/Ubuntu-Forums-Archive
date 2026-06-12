---
title: "No ethernet, wifi adapter works fine beed some help"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by jim135 on 2016-02-20
I have been at this for hours, I have some quad core xeons on supermicro server boards and tried to "upgrade" to a hardwired connection over the wifi. It says that its connected but, there is no functioning Internet. The WIFI adapter is currently unplugged

I keep getting this:

 dmesg | grep eth
[    0.146759] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c3a4b0), AE_ALREADY_EXISTS (20150619/psparse-536)
[    2.156498] e1000e 0000:0d:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:30:48:64:83:f5
[    2.156502] e1000e 0000:0d:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.156573] e1000e 0000:0d:00.0 eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[   22.848620] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.028401] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.424951] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

and this 

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:64:83:f5  
          inet6 addr: fe80::230:48ff:fe64:83f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3737509 (3.7 MB)  TX bytes:12752 (12.7 KB)
          Interrupt:16 Memory:de100000-de120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:415680 (415.6 KB)  TX bytes:415680 (415.6 KB)

and this 

lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 00
       serial: 00:30:48:64:83:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.5-7 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:26 memory:de100000-de11ffff ioport:2000(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 00
       serial: 00:30:48:64:83:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.5-7 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:26 memory:de100000-de11ffff ioport:2000(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


Any help is hugely appreciated as this is extremely frustrating on my first big build

---

### Post by chili555 on 2016-02-20
Is this a server, meaning that you configure networking manually or a desktop install using Network Manager? If the latter, as I suspect, may we see:```
dmesg | grep -e eth0 -e e100
```If the former, may we see:```
cat /etc/network/interfaces
```

---

### Post by jim135 on 2016-02-20
I did both, I am using some server MB from Supermicro with Intel Ethernet so, I wasn't sure if both may help you. I am running 15.10 desktop os

:~$ dmesg | grep -e eth0 -e e100
[    0.000000] BRK [0x01ce1000, 0x01ce1fff] PGTABLE
[    0.147240] pci 0000:0d:00.0: reg 0x10: [mem 0xde100000-0xde11ffff]
[    0.147488] pci 0000:00:1c.4:   bridge window [mem 0xde100000-0xde1fffff]
[    0.201870] pci 0000:00:1c.4:   bridge window [mem 0xde100000-0xde1fffff]
[    0.201939] pci_bus 0000:0d: resource 1 [mem 0xde100000-0xde1fffff]
[    2.039243] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.5-k
[    2.039245] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    2.039446] e1000e 0000:0d:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.149469] e1000e 0000:0d:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:30:48:64:83:f5
[    2.149473] e1000e 0000:0d:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.149545] e1000e 0000:0d:00.0 eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[   30.796650] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.980459] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.188955] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   33.189092] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


second request
 cat /etc/network/interfaces

auto lo
iface lo inet loopback

Thank you!!!

---

### Post by chili555 on 2016-02-20
> [ 33.188955] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 33.189092] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes readyThis pretty much looks like it's all set. Let's see what Network Manager is doing:```
cat /var/log/syslog | grep etwork | tail -n25
```As this will be lengthy, please paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by jim135 on 2016-02-20
Here is the link 

[http://paste.ubuntu.com/15150938/](http://paste.ubuntu.com/15150938/)

---

### Post by gordintoronto on 2016-02-21
What is the DHCP server? Ifconfig says you have an ipv6 address, but no ipv4 address.

---

### Post by chili555 on 2016-02-21
> **jim135 said:**
> Here is the link 

[http://paste.ubuntu.com/15150938/](http://paste.ubuntu.com/15150938/)I am not quite sure what is (not) going on here. Please try:```
sudo service network-manager stop
sudo dhclient eth0
```Please copy and paste the result here.

---

