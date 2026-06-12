---
title: "Statically configured connection doesn't reconnect"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by ChrisMP1 on 2008-02-27
My computer needs to have a statically configured IP address, because I redirect a few ports to it through the router. The problem is, with dynamic configuration, if the connection is dropped, the computer automatically reconnects. On a static configuration, I have to drop to a terminal and "sudo ifdown wlan0 && sudo ifup wlan0" to get a connection. Can I make the network manager applet (if that's what is doing it) work with a static connection. Is there another way?

---

### Post by Iowan on 2008-02-27
Post **ifconfig **and contents of **/etc/network/interfaces**.

and **iwconfig**

---

### Post by ChrisMP1 on 2008-02-27
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1B:38:B9:AE:C8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8764 (8.5 KB)  TX bytes:8764 (8.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:57:A2:69  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe57:a269/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15509765 (14.7 MB)  TX bytes:2711006 (2.5 MB)
          Interrupt:22 Memory:51300000-51310000 

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.60
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk ***censored for obvious reasons***
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid pvlnet

auto wlan0

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"pvlnet"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: **censored**   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by ChrisMP1 on 2008-02-27
Update: New problem. I can't connect when manually configured. I can only get a connection when using DHCP.

```

15:23 chris> ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.60 icmp_seq=3 Destination Host Unreachable
From 192.168.1.60 icmp_seq=5 Destination Host Unreachable
From 192.168.1.60 icmp_seq=6 Destination Host Unreachable
From 192.168.1.60 icmp_seq=8 Destination Host Unreachable
From 192.168.1.60 icmp_seq=9 Destination Host Unreachable

```

---

### Post by ChrisMP1 on 2008-03-02
Update: I ditched nm-applet and am managing the network myself. It's working fine.

---

