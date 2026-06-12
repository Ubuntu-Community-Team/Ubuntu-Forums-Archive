---
title: "Suuuuuuuupppper NOOOOOBBBB!!!"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Graffight on 2008-06-26
OK...so i figured out how to partition my drive, and i figured out how to install the ubuntu, but i can't get online, wired or wireless. i have version 6.0. any help :-(

---

### Post by chili555 on 2008-06-26
Open a terminal at Applications -> Accessories -> Terminal and type:```
sudo lshw -C network
```We will find some details there that will help us proceed.

---

### Post by tamoneya on 2008-06-26
also post the output of ```
ifconfig
``` This is also typed in terminal.

Since you have no internet and cant copy out of terminal into the forums you should direct it into a file on say a USB drive and the post it to the terminal:

```
cd /media/flashdrive
sudo lshw -C network > lshw.txt
ifconfig > ifconfig.txt
```

EDIT: I also wanted to add that it is best if you pick a more descriptive title.  It helps out everybody in the forum and makes people happier in general.  In you case I would go with something like: "My network doesnt work".  Then you could add that you are a "noob" in the post.  Also the a lot of the people in the forum tend to think of the word noob as a little derogatory and demeaning.  Instead we prefer that you say "Im new to linux".

---

### Post by Graffight on 2008-06-26
Thank you kindly, i'm at work right now but i'll post that info as soon as i can get it!

---

### Post by Graffight on 2008-06-28
ok so when i actually did the full install i was able to get online for a little bit, then i disconnected the ethernet and tried to set up wireless and then the ethernet didn't work anymore.

ifconfig results:
ath0      Link encap:Ethernet  HWaddr 00:0b:6b:36:f5:8e  
          inet6 addr: fe80::20b:6bff:fe36:f58e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:0b:6b:36:f5:8e  
          inet addr:169.254.8.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:90:f5:3f:2e:d9  
          inet6 addr: fe80::290:f5ff:fe3f:2ed9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:21 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10891 (10.6 KB)  TX bytes:10891 (10.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0B-6B-36-F5-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1734 errors:0 dropped:0 overruns:0 frame:297
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:147917 (144.4 KB)  TX bytes:4170 (4.0 KB)
          Interrupt:20

---

### Post by Graffight on 2008-06-28
Results for sudo lshw -C network

*-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:3f:2e:d9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:0a:05.0
       logical name: wifi0
       version: 01
       serial: 00:0b:6b:36:f5:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

