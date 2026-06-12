---
title: "cannot connect to router or internet"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by louislepperd on 2008-09-25
hello
i have recently installed xubuntu(dual boot with xp) on a computer and have inserted all correct ip addresses etc but it will not ping the internet or my gateway(router Netgear ngr614 v6).(wired)(the xp can connect fine)
the settings that i add for a windows computer to connect to my network are:
ip address:192.168.8.**(btw the ip i want for this computer is 192.168.8.22)
subnet mask:255.255.255.0
gateway:192.168.8.2
dns servers:
192.168.1.1
202.27.156.72
202.27.158.40

the results from ifconfig are:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:ab:a1:08  
          inet addr:192.168.8.22  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:feab:a108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39547 (38.6 KB)  TX bytes:39547 (38.6 KB)

---

### Post by superprash2003 on 2008-09-25
unable to ping your router?192.168.8.2 which pc or router is that??

---

### Post by louislepperd on 2008-09-25
192.168.8.2 is my router(netgear ngr614 v6) with a modem connected to it.(all thru ethernet)

---

### Post by Baelus on 2008-09-25
Using the 'route' command in terminal, does that show a default gateway(gw) to eth0. If not you can try this:

```
sudo route add default gw 192.168.8.2 eth0
```

---

### Post by louislepperd on 2008-09-26
hi when I run route I get:
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.8.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.8.2     0.0.0.0         UG    100    0        0 eth0

---

### Post by Idefix82 on 2008-09-26
What is the output from
```
lshw -C network
```

---

### Post by louislepperd on 2008-09-26
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:ab:a1:08
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.8.22 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by willca on 2008-09-26
can you post your /etc/network/interfaces

also can you try pinging yourself, eth0 I mean.

then run this..

arp -a

---

### Post by louislepperd on 2008-09-26
hello this is /etc/network/interfaces:
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.8.22
netmask 255.255.255.0
gateway 192.168.8.2

auto eth0

---

### Post by louislepperd on 2008-09-26
this is my ping:
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.038 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.031/0.035/0.039/0.006 ms

---

### Post by louislepperd on 2008-09-26
and this is arp:
arp -a
? (192.168.8.2) at <incomplete> on eth0

---

### Post by superprash2003 on 2008-09-26
what is the output of ping 192.168.8.2 ?

---

### Post by louislepperd on 2008-09-26
ping 192.168.8.2
PING 192.168.8.2 (192.168.8.2) 56(84) bytes of data.
From 192.168.8.22 icmp_seq=1 Destination Host Unreachable
From 192.168.8.22 icmp_seq=4 Destination Host Unreachable
From 192.168.8.22 icmp_seq=5 Destination Host Unreachable
From 192.168.8.22 icmp_seq=7 Destination Host Unreachable
From 192.168.8.22 icmp_seq=8 Destination Host Unreachable
From 192.168.8.22 icmp_seq=9 Destination Host Unreachable

--- 192.168.8.2 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8001ms
, pipe 3



btw this happens when i ping any computer on my network

---

### Post by Baelus on 2008-09-26
Have you tried a different network cable?

---

### Post by louislepperd on 2008-09-26
no i havent but its dual boot with xp and the xp can connect fine

---

### Post by superprash2003 on 2008-09-28
have you tried via DHCP?? is DHCP enabled in your router?

---

### Post by louislepperd on 2008-09-30
yes i have tried dhcp(it is enabled on my router)
but it still did not work
thanks in advance
louis

---

### Post by louislepperd on 2008-10-01
btw i tryed dual booting xubuntu(different cd same iso)
on a different computer on my network and it worked fine,
then i reinstalled it on the one that i am trying to get working but it still does not work!:(

---

### Post by Baelus on 2008-10-02
To recap with the new installation, please post output of:

```
cat /etc/network/interfaces
```

```
cat /etc/resolv.conf
```

```
ifconfig
```

```
route
```

Let's see if we can spot something.:shock:

---

### Post by louislepperd on 2008-10-07
yce@joyce-linux-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.8.73
netmask 255.255.255.0
gateway 192.168.8.2

auto eth0
joyce@joyce-linux-desktop:~$ cat /etc/resolv.conf
nameserver 202.27.156.72
nameserver 202.27.158.40
nameserver 192.168.1.1
nameserver 192.168.8.2
joyce@joyce-linux-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:ab:a1:08  
          inet addr:192.168.8.73  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:feab:a108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1756 (1.7 KB)  TX bytes:1756 (1.7 KB)

joyce@joyce-linux-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.8.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         gw              0.0.0.0         UG    100    0        0 eth0
joyce@joyce-linux-desktop:~$

---

### Post by Baelus on 2008-10-07
> joyce@joyce-linux-desktop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:19:21:ab:a1:08
inet addr:192.168.8.73 Bcast:192.168.8.255 Mask:255.255.255.0
**inet6 addr**: fe80::219:21ff:feab:a108/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xe400 

Only thing I can guess at is maybe disasble ipv6?

[http://ubuntuforums.org/showthread.php?t=694922&highlight=howto+disable+ipv6]("http://ubuntuforums.org/showthread.php?t=694922&highlight=howto+disable+ipv6")

Or pass 'noapic' to the kernel in grub.

Other than that I have no idea. :(

---

