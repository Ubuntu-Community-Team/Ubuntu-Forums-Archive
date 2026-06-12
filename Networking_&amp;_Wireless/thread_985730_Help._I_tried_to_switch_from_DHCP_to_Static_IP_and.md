---
title: "Help. I tried to switch from DHCP to Static IP and screwed up all my settings."
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by formulaic on 2008-11-17
I'm running Ubuntu (Hardy) on a laptop that connects to the internet via a wireless router. In an effort to switch from DHCP to a static IP address, I have accidentally screwed up my /etc/network/interfaces and /etc/resolv.conf, and uninstalled dhcp3-client (and its dependencies). I also can no longer see my wireless network manager and can't connect to anything.

Here is some information:

$ ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:16:d3:28:21:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x2000 Memory:ee000000-ee020000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111785 (109.1 KB)  TX bytes:111785 (109.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:9c:06:d1  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe9c:6d1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114356 (111.6 KB)  TX bytes:168766 (164.8 KB)
wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-9C-06-D1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


# /etc/network/interfaces

> auto lo
iface lo inet loopback

allow-hotplug wlan0
iface wlan0 inet static
address 192.168.1.17
netmask 255.255.255.0
gateway 192.168.1.1
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid XX

auto wlan0

# /etc/resolv.conf
> nameserver 192.168.1.1

$ ping 64.208.34.100> 
PING 64.208.34.100 (64.208.34.100) 56(84) bytes of data.
From 192.168.1.17 icmp_seq=2 Destination Host Unreachable
From 192.168.1.17 icmp_seq=3 Destination Host Unreachable
From 192.168.1.17 icmp_seq=4 Destination Host Unreachable

Please ask questions if it will help; I will respond within 10 minutes of your post! I'm desperate. Thanks!

---

