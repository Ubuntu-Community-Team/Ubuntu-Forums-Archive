---
title: "Bizarre networking problem in Ubuntu Server"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by Deidgar on 2008-07-09
I've installed Ubuntu Server on a new server in the office and can't diagnose a network issue that's preventing me accessing the internet.  Basically I can resolve hosts to IP addresses, but can't ping them so something is blocking me, but I can't figure out what.  Would really appreciate any ideas anyone has to solve the problem.  Following information for diagnosis:

```
INTERFACES

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 193.168.1.200
        netmask 255.255.255.0
        network 193.168.1.0
        broadcast 193.168.1.255
        gateway 193.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 193.168.1.1 210.22.70.3 210.22.70.227
        dns-search PBNet

```

```


RESOLV.CONF

nameserver 193.168.1.1
nameserver 210.22.70.3
nameserver 210.22.70.227

```

```
IFCONFIG -a

eth0      Link encap:Ethernet  HWaddr 00:30:1b:46:b8:d8
          inet addr:193.168.1.200  Bcast:193.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:239343 (233.7 KB)  TX bytes:276768 (270.2 KB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thanks in advance for any suggestions.

---

### Post by superprash2003 on 2008-07-09
do you have firestarter or anything similar running?

---

