---
title: "Can't ping gateway with Wireless Adapters"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by Al Grant on 2015-01-11
Hi All,

I am on Ubuntu 14 (32 bit).

If I connect to my ADSL modem with ethernet cable life is good and I the network works as expected. This is a static IP.

When I try to connect with any of my USB wireless adapters (DHCP) I can ping the likes of Google (8.8.8.8) but cant ping anything on the LAN and its driving me nuts.

Here is some info when the connection is eth0 and working:

ifconfig
```

al@Sanyo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:a3:86:42
          inet addr:192.168.55.200  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fea3:8642/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13018 (13.0 KB)  TX bytes:7678 (7.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:331439 (331.4 KB)  TX bytes:331439 (331.4 KB)

wlan1     Link encap:Ethernet  HWaddr 00:c0:ca:57:29:00
          inet addr:192.168.55.56  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe57:2900/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7942326 (7.9 MB)  TX bytes:1408272 (1.4 MB)

```

ping
```

al@Sanyo:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=45.8 ms
^C
--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 45.813/45.813/45.813/0.000 ms
al@Sanyo:~$ ping 192.168.55.1
PING 192.168.55.1 (192.168.55.1) 56(84) bytes of data.
64 bytes from 192.168.55.1: icmp_seq=1 ttl=255 time=0.422 ms
64 bytes from 192.168.55.1: icmp_seq=2 ttl=255 time=0.237 ms
^C
--- 192.168.55.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.237/0.329/0.422/0.094 ms

```

route
```

al@Sanyo:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Vigor.router    0.0.0.0         UG    0      0        0 wlan1
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.55.0    *               255.255.255.0   U     0      0        0 eth0
192.168.55.0    *               255.255.255.0   U     9      0        0 wlan1
al@Sanyo:~$

```

And when the eth0 is unplugged and I am wireless:

ping
```

al@Sanyo:~$ ping 192.168.55.1
PING 192.168.55.1 (192.168.55.1) 56(84) bytes of data.
^C
--- 192.168.55.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1006ms

```

/etc/network/interfaces
```

al@Sanyo:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto wlan1

auto eth0
iface eth0 inet static
address 192.168.55.200
netmask 255.255.255.0
network 192.168.55.0
broadcast 192.168.55.255
gateway 192.168.55.1
dns-nameservers 192.168.55.1 8.8.8.8

```

IPTables
```

al@Sanyo:~$ sudo iptables -L
[sudo] password for al:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
al@Sanyo:~$

```

Please help!!

Thanks

-Al

---

### Post by Al Grant on 2015-01-11
Just to add to the puzzle, when I reboot the wireless adapter wlan1 shows up - but I cant list any wireless networks in network manager, nor with sudo iwlist wlan1 s.

Something weird is going on.

---

### Post by chili555 on 2015-01-11
> al@Sanyo:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan1
[COLOR="#FF0000"]iface wlan1 inet what???[/COLOR]

auto eth0
iface eth0 inet static
address 192.168.55.200
netmask 255.255.255.0
network 192.168.55.0
broadcast 192.168.55.255
gateway 192.168.55.1
dns-nameservers 192.168.55.1 8.8.8.8Is Network manager handling wlan1 or is /etc/network/interfaces? Where is the SSID, encryption, et al declared?

---

### Post by Al Grant on 2015-01-12
I have changed it (see below) and rebooted - but the problem of not being able to ping gateway (or other lan clients) persists.

Other PC's on the lan dont have the same problem.

```

al@Sanyo:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.55.1    0.0.0.0         UG    0      0        0 wlan1
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.55.0    *               255.255.255.0   U     0      0        0 eth0
192.168.55.0    *               255.255.255.0   U     9      0        0 wlan1
al@Sanyo:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.55.200
netmask 255.255.255.0
network 192.168.55.0
broadcast 192.168.55.255
gateway 192.168.55.1
dns-nameservers 192.168.55.1 8.8.8.8
 

al@Sanyo:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=45.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=45.7 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 45.564/45.656/45.749/0.232 ms
al@Sanyo:~$ ping 192.168.55.1
PING 192.168.55.1 (192.168.55.1) 56(84) bytes of data.
From 192.168.55.200 icmp_seq=1 Destination Host Unreachable
From 192.168.55.200 icmp_seq=2 Destination Host Unreachable
From 192.168.55.200 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.55.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4024ms
pipe 3
al@Sanyo:~$ 

```

-Al

---

### Post by chili555 on 2015-01-12
Al, I repeat:> Is Network Manager handling wlan1 or is /etc/network/interfaces? Where is the SSID, encryption, et al declared?If you are expecting NM to handle wireless and /etc/network/interfaces to handle ethernet, I'm not sure that's realistic to expect. If it were me, I'd set the static IP for ethernet in NM and be done.

---

### Post by Al Grant on 2015-01-12
I fixed it with :

```

ifconfig eth0 down

```

---

### Post by Al Grant on 2015-01-12
I fixed it with :

```

ifconfig eth0 down

```

---

### Post by Al Grant on 2015-01-12
I fixed it with :

```

ifconfig eth0 down

```

---

