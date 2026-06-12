---
title: "Static IP: Ethernet interface appears twice, one causes problems."
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by aaronshenhao on 2017-07-16
I am using **Ubuntu 16.04**. The static IP is working, but the Ethernet interface seems to appear twice as *enp2s0* (does not work) and *ifupdown(enp2s0)*. I have also set up static IP for the wireless interface, but it does not have this problem.

The computer occasionally connects to* enp2s0* mysteriously, especially after *network.service* is restarted. I get an error that says something similar to "This webpage cannot be found", which looks like a DNS issue. To fix this, I have to either click on *ifupdown(enp2s0)* on the top right or run sudo ifdown enp2s0 then *sudo ifup enp2s0*. Once connected to *ifupdown(enp2s0)*, *enp2s0* disappears. **Why is this happening and how do I prevent it?**

To set the static IP, I first changed */etc/network/interfaces* to allow the Ethernet and wireless interface to have static IPs. I went to */etc/NetworkManager/NetworkManager.conf* and set *[ifupdown] managed=true*.

***/etc/network/interfaces***
```
# interfaces(5) file used by ifup(8) and ifdown(8)
# The loopback network interface
auto lo
iface lo inet loopback

# Assign static IP
auto enp2s0
iface enp2s0 inet static
address 192.168.0.218
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4

auto wlp3s0
iface wlp3s0 inet static
address 192.168.0.218
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```

***/etc/NetworkManager/NetworkManager.conf***
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true
```

***ip link***
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 38:2c:4a:1f:02:be brd ff:ff:ff:ff:ff:ff
3: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 18:cf:5e:27:2b:6a brd ff:ff:ff:ff:ff:ff
```

[I][B]ifconfig
[/B][/I]```
enp2s0    Link encap:Ethernet  HWaddr 38:2c:4a:1f:02:be  
          inet addr:192.168.0.218  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3b69:a581:1b73:66f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96465 errors:0 dropped:9 overruns:0 frame:0
          TX packets:80453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52379264 (52.3 MB)  TX bytes:14359028 (14.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:3058512 (3.0 MB)  TX bytes:3058512 (3.0 MB)

wlp3s0    Link encap:Ethernet  HWaddr 18:cf:5e:27:2b:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:83028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86707469 (86.7 MB)  TX bytes:8884239 (8.8 MB)
```

Thank you for your time :D

---

### Post by chili555 on 2017-07-16
Please see my reply here: [https://askubuntu.com/questions/936649/static-ip-ethernet-network-interface-appears-twice-how-to-remove](https://askubuntu.com/questions/936649/static-ip-ethernet-network-interface-appears-twice-how-to-remove)

---

