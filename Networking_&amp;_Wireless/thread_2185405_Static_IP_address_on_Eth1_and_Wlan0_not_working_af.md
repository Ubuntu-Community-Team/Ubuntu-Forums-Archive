---
title: "Static IP address on Eth1 and Wlan0 not working after a boot at times"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by mikeluter49 on 2013-11-02
I have setup my interfaces as listed below but at times after a reboot or shutdown it will not come up with a ip

auto lo
iface lo inet loopback
iface eth0 inet dhcp
allow-hotplug eth1
iface eth1 inet static
  address 192.168.42.1
  netmask 255.255.255.0
  post-up ip addr add dev eth1 192.168.42.49/24
  pre-down ip addr del dev eth1 192.168.42.49/24
allow-hotplug wlan0
iface wlan0 inet static
  address 192.168.43.1
  netmask 255.255.255.0
  post-up ip addr add dev wlan0 192.168.43.89/24
  pre-down ip addr del dev wlan0 192.168.43.89/24
up iptables-restore < /etc/iptables.ipv4.nat

:?:](*,)

---

### Post by mikeluter49 on 2013-11-02
this is what i get after a reboot

eth0      Link encap:Ethernet  HWaddr b8:27:eb:5c:ea:d2
          inet addr:172.16.1.135  Bcast:172.16.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:107421 (104.9 KiB)  TX bytes:9155 (8.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:06:a7:e0:17:c3
          inet addr:192.168.42.49  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2840 (2.7 KiB)  TX bytes:140 (140.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:2f:50:4d:be
          inet addr:192.168.43.1  Bcast:192.168.43.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mikeluter49 on 2013-11-02
it worked on wlan0 but not on eth1
i have checked around and can not find anyone that has posted a problem like this one
any help would be great
many thanks
Mike

---

