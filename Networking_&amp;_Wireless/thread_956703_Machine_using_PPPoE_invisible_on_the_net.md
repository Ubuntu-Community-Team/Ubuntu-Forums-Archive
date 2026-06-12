---
title: "Machine using PPPoE invisible on the net"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by ripdajacker on 2008-10-23
Hello

I've setup a ubuntu 8.10 box (same issue with 8.04) with pppoe, using the 

The hardware is:
AMD Sempron 3400+
ASUS K8N-E motherboard
1GB ram and a brand new 160GB harddrive.

```
ppoeconf
``` command.

I've succesfully been able to browse the internet, send mail, even download stuff with bittorrent, but I cannot access the machine ie. by ssh'ing to it from a remote location using it's ip.

I can, however, access it using it's ip locally i.e. ```
ssh 78.156.123.13
``` from the machine logs on, but the same command from another network does not work. I cannot even ping it.

I have two interfaces, eth0 and ppp0.

ifconfig gives:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:49:b6:f9  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe49:b6f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14608002 errors:2 dropped:0 overruns:0 frame:2
          TX packets:12607770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:689991432 (689.9 MB)  TX bytes:2352597887 (2.3 GB)
          Interrupt:22 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:48386 (48.3 KB)  TX bytes:48386 (48.3 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:78.156.123.13  P-t-P:78.156.96.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:14605137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12604789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:368416828 (368.4 MB)  TX bytes:2075169976 (2.0 GB)
```


```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```

NetworkManager is disabled, and so is the firewall.

There is only one network card, a onboard 10/100 ethernet card.

Thanks in advance

---

