---
title: "Slow connection buildup"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by rpjknoop on 2008-09-16
Hello,

I am using two identical PC's both with Ubuntu installed. One has Ubuntu 7 desktop edition and the other Ubuntu 8 server edition. Both of these PC's function as a server within my local LAN. They provide an FTP server, Web server and some other services. Both machines are the same in settings (except the fixed ip ofcourse). The problem I have is that with the Ubuntu 8 machine connection buildup seems to be very slow. Uploading to the proftpd server running on it of about a 100 files of a few kb can take minutes on this one while the other handles it in seconds. When copying large files the difference is minimal. Proftpd.conf is the same on both machines. Other services besides FTP seem to have similar problems. A program I wrote myself for instance has a listen socket, processes data received from there and then sends it to another server on a new outgoing socket. Again this software works fine on the old Ubuntu but has delays on the new machine until after a while it runs fine(weird; maybe something with buffering?). Pinging the machine goes quickly though, about 0.2 ms. CPU load is less then 3% most of the time as well. Anyone who has any idea what could cause this, help would be greatly appreciated? 

Some outputs:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:55:e4:64
          inet addr:192.168.201.233  Bcast:192.168.201.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2007387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:331328470 (315.9 MB)  TX bytes:136088390 (129.7 MB)
          Interrupt:222 Base address:0xc000

```

lshw -C network:
```
*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:25:55:e4:64
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.201.233 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

---

### Post by rpjknoop on 2008-09-17
Anyone who can help?

---

### Post by rpjknoop on 2008-09-29
I did another test on a totally different machine. I get the same slow responses when downloading files with proftpd. I performed all hints on improving this, like disable the IPV6, UseReverseDNS and IdentLookups.

Does anyone use Proftpd in combination with Ubuntu 8.04?

I have no problem what so ever with Ubuntu 7.10.

So what is the difference :confused:?

---

