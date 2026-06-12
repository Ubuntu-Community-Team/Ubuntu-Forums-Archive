---
title: "internet not working, only VPN is visible"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by govinda3 on 2014-10-20
I am new to ubuntu I have installed ubuntu on my computer ,now I am not getting ethernet ( trying to connect wired connection ) option in my network manager .only VPN is option is visible please someone help me.

here are few outputs:

```

   root@Govi:/home/govinda# vi /etc/network/interfaces

## interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider
auto eth0
iface eth0 inet manual


#auto lo
#iface lo inet loopback


#auto eth0
#iface eth0 inet dhcp



```

```

root@Govi:/home/govinda# sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:b3:5e:ec:5f  
          inet6 addr: fe80::225:b3ff:fe5e:ec5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9104 (9.1 KB)  TX bytes:3914 (3.9 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37480 (37.4 KB)  TX bytes:37480 (37.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:dd:ca:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B


```

---

