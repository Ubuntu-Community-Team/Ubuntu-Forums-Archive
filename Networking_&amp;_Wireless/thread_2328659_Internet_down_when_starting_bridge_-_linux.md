---
title: "Internet down when starting bridge - linux"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by joaoamaroscp on 2016-06-23
So I'm starting a bridge on my linux computer. When I run this script:


```
#!/bin/sh


ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0


brctl addbr bridge


brctl addif bridge eth0
brctl addif bridge eth1


ifconfig bridge up


dhclient bridge

```

I can't access any website.


"ifconfig" before script:


```
eth0      Link encap:Ethernet  HWaddr 00:01:c0:15:c1:1b
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:c0ff:fe15:c11b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:541592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:742359477 (742.3 MB)  TX bytes:215896 (215.8 KB)


eth1      Link encap:Ethernet  HWaddr 00:01:c0:15:c3:1e
          inet6 addr: fe80::201:c0ff:fe15:c31e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:125604 (125.6 KB)  TX bytes:304131282 (304.1 MB)

```

"ifconfig" after script:


```
eth0      Link encap:Ethernet  HWaddr 00:01:c0:15:c1:1b
          inet6 addr: fe80::201:c0ff:fe15:c11b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:545319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:746310084 (746.3 MB)  TX bytes:393448 (393.4 KB)


eth1      Link encap:Ethernet  HWaddr 00:01:c0:15:c3:1e
          inet6 addr: fe80::201:c0ff:fe15:c31e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:126265 (126.2 KB)  TX bytes:304167552 (304.1 MB)


bridge    Link encap:Ethernet  HWaddr 00:01:c0:15:c1:1b
          inet addr:192.168.1.171  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:c0ff:fe15:c11b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6252 (6.2 KB)  TX bytes:14889 (14.8 KB)

```

How can I change my script in order to enable the internet connection?

---

### Post by TheFu on 2016-06-23
Never tried doing it the way you are. Usually just add the bridge to the /etc/network/interfaces file.

```
# ####################################
# The primary network interface
auto eth0
iface eth0 inet manual

# ####################################
auto br0
iface br0 inet static
  address 172.22.22.6
  gateway 172.22.22.1
  netmask 255.255.255.0
  broadcast 172.22.22.255
  # mtu 9014
  dns-nameservers 172.22.22.1
  dns-search example.lan
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

The key thing is NOT to use eth0 for anything - use the bridge, br0, going forward.  Not sure how useful a bridge with DHCP is, but you can try it.

---

