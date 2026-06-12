---
title: "One interfaces, two IP (alias), server 14.04, two gateway via routing"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by sys.adimix on 2014-11-22
I just found out [URL="https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1301015"]```
sudo /etc/init.d/networking restart
```[/URL] is not working anymore in ubuntu 14.04. Since I use server version, and configured it through ssh, there is no network-manager or NetworkManager for me. Instead I use ```
sudo ifdown eth0 && sudo ifup eth0
``` to restart networking.

I have two gateway, one 192.168.0.1, a router connect to broadband internet and wireless bridging to the next building. The wireless AP Client Router IP address is 192.168.200.12 in my network. As client AP from the next building, this router geting manual IP 192.168.100.12. Network in the next building is setup with IP address 192.168.100.0/24 and the the next building wireless AP is 192.168.100.11.

So here is my network configuration in /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface   eth0 inet static
address 192.168.0.8
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1
post -up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1
route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.200.12

auto eth0:1
iface   eth0:1 inet static
address 192.168.200.8
netmask 255.255.255.0
broadcast 192.168.200.255


```

After i restart the network, here the result from ifconfig and netstat -r -n

```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2145 errors:0 dropped:74 overruns:0 frame:0
          TX packets:716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191601 (191.6 KB)  TX bytes:102650 (102.6 KB)

eth0:1    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.200.8  Bcast:192.168.200.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:416590 (416.5 KB)  TX bytes:416590 (416.5 KB)

virbr0    Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0
192.168.200.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

Only one routing command is applied after ifup. Everytime the server boot, I have to add the second gateway manually.

What is the mistake that I make in my configuration?

Most of the post is either dealing with alias, multiple network card or dealing with multiple gateway only. Does the second route command (gateway 192.168.200.12) is not working because I'm using alias IP address?

Thanks for any response.

ps: ```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
``` remove my routing table, there will be no gateway if I restart networking using this command.

---

### Post by sys.adimix on 2015-07-04
My currently /etc/network/interfaces. Its working after I fix some typo in previous post. Thread will be mark solved. Also as note, I assign reserve IP address in DHCP server for the my Ubuntu server MAC address.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.0.8
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1
route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.200.12


auto eth0:1
iface eth0:1 inet static
address 192.168.200.8
netmask 255.255.0.0
network 192.168.200.0
broadcast 192.168.200.255
#gateway 192.168.200.12
#dns-nameserver 192.168.0.1
post-up route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.200.12


```

---

