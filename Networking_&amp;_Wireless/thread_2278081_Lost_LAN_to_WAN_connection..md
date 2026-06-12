---
title: "Lost LAN to WAN connection."
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by odror on 2015-05-13
In the process of installing bridge network I lost my LAN (eth0) to WAN (eth1) connection.

I removed network manager
I disabled IPV6

I am still not have a connection.

/etc/network/interfaces:
> [FONT=Courier New]auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth0
#iface eth0 inet manual
iface eth0 inet static
        address 192.168.0.1
        broadcast 192.168.0.255
        netmask 255.255.255.0
        dns-nameservers 8.8.8.8 8.8.4.4[/FONT]


route:
> [FONT=Courier New]Kernel IP routing table
Destination              Gateway                    Genmask         Flags Metric Ref    Use Iface
default                    xxx 0.0.0.0          UG     0      0        0 eth1
x.x.24.0                  *                255.255.248.0   U     0      0        0 eth1
link-local                 *                255.255.0.0     U     1000   0        0 eth0
172.17.0.0              *                255.255.0.0     U     0      0        0 docker0
192.168.0.0            *                255.255.255.0   U     0      0        0 eth0
192.168.122.0        *                255.255.255.0   U     0      0        0 virbr0[/FONT]


ifconfig 
> 
[FONT=Courier New]docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 78:e3:b5:88:8a:ae  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132898485 (132.8 MB)  TX bytes:49621 (49.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:23:56:3c:20:67  
          inet addr: x.x.29.12  Bcast:255.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:970492 (970.4 KB)  TX bytes:208560 (208.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6115925 (6.1 MB)  TX bytes:6115925 (6.1 MB)

lxcbr0    Link encap:Ethernet  HWaddr 46:91:fa:7a:c9:37  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5394 (5.3 KB)

virbr0    Link encap:Ethernet  HWaddr c6:6f:b5:1e:c0:b1  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/FONT]


to me everything looks OK except the default destination for eth0 "link-local" I removed IPV6 and I still have it. I am not sure if it is the one that cases the problem

Any help will be appreciated.

---

### Post by tgalati4 on 2015-05-13
Post the output of:

```
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by odror on 2015-05-13
problem fixed. It was the firewall. I am using firebuider There was an error compiling the rules. Thus my firewall was incomplete.

---

