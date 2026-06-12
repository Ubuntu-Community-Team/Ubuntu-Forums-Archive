---
title: "Issues with sub-interface on ubuntu 14.04"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by abhi-soaphy on 2016-12-29
Hi,

I am having some issues with creating the sub interfaces on Ubuntu 14.04. I have two interfaces em1 and em2. em1 is connected to internet and on em2 i have two sub interfaces created each on sepearate private subnets for openstack. It worked well for me when i configured but after reboot i cant access anything on em2.200 subnet nothing has changed i verified the configurations and all looks ok for me.

I used vconfig to create the sub-interfaces on my servers below is my /etc/network/interfaces output...

auto em2.100
iface em2.100 inet static
       address 192.168.79.254
       netmask 255.255.255.0
       vlan-raw-device em2


auto em2.200
iface em2.200 inet static
      address 172.18.0.1
      netmask 255.255.255.0
      vlan-raw-device em2.100

em2.100 works fine i see the traffic using the tcpdump but nothing shows up on the em2.200 ??  below is the ifconfig output from the server..

em2       Link encap:Ethernet  HWaddr 9c:8e:99:1a:11:55
          inet6 addr: fe80::9e8e:99ff:fe1a:1155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128090 errors:0 dropped:7 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7971205 (7.9 MB)  TX bytes:20808 (20.8 KB)
          Memory:c0460000-c047ffff


em2.100   Link encap:Ethernet  HWaddr 9c:8e:99:1a:11:55
          inet addr:192.168.79.254  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::9e8e:99ff:fe1a:1155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1777670 (1.7 MB)  TX bytes:648 (648.0 B)


em2.200   Link encap:Ethernet  HWaddr 9c:8e:99:1a:11:55
          inet addr:172.18.0.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::9e8e:99ff:fe1a:1155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:2664 (2.6 KB)



Can someone shed some light on this issues please....

Thanks,
A

---

