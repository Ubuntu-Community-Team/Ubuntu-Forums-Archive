---
title: "wireless. Gutsy upgrade. WG511T"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by kotak07 on 2007-11-06
yeah ive had ubuntu for about 3-4 weeks now and i had feisty installed from the Live CD but once i installed it i upgraded it to gutsy and i have the WG511T card and it worked great. I have the Restricted HAL driver and everything but since the past couple of days..ive had a problem with verizon dsl..at first my desktop and this laptop didnt get any internet connection..but then they "fixed" it and my desktop gets it now..and its pretty aright internet..but my ubuntu 7.10 gutsy doesnt get the internet. It says its connected and sometimes the pidgin IM works but then it disconnects. and I cant get on the internet period. Right now im working from the LiveCD so im guessing that theres nothing wrong with the router/dsl/signal cuz the liveCD picks it up. So whats wrong in gutsy? it worked before why doesnt it work now..im in roaming mode and everything. and when i use a static IP it just doesnt work...btw i need help fast on this. I'm a student so i can't be long without internet due to school work and etc.

---

### Post by BigMickB on 2007-11-06
I wish you luck my friend. I have been looking on this forum to a similar problem for quite some time now - still no resolution found.  Im using Feisty Fawn 7 - 04. I wish someone could help me get my internet going again on Linux. 'Til then its Bill the man!!

---

### Post by kotak07 on 2007-11-06
yeah i have no idea why it wouldve stopped all of a sudden. any mods or anyone have a solution to this problem?

---

### Post by kotak07 on 2007-11-07
here is "lshw -C network"
```
root@Neals-Laptop:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:0e:61:b0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:07:00.0
       logical name: wifi0
       version: 01
       serial: 00:14:6c:7f:89:6d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=10.0.0.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


```

"iwconfig"

```

neal@Neals-Laptop:~$ su -
Password: 
root@Neals-Laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Verizon"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:57:96:CE   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6745-4C74-973B-C5C7-24F9-D8B7-409F-0A4F   Security mode:restricted
          Power Management:off
          Link Quality=35/70  Signal level=-59 dBm  Noise level=-94 dBm
          Rx invalid nwid:5366  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by kotak07 on 2007-11-07
heres sudo ip route

```

root@Neals-Laptop:~# sudo ip route
10.0.0.0/24 dev ath0  proto kernel  scope link  src 10.0.0.2 
169.254.0.0/16 dev ath0  scope link  metric 1000 
default via 10.0.0.1 dev ath0 

```

and heres ifconfig

```

root@Neals-Laptop:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:7F:89:6D  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe7f:896d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:2 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:218303 (213.1 KB)  TX bytes:39625 (38.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:0E:61:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10152 (9.9 KB)  TX bytes:10152 (9.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-7F-89-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20428 errors:0 dropped:0 overruns:0 frame:8594
          TX packets:852 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2644167 (2.5 MB)  TX bytes:80975 (79.0 KB)
          Interrupt:16 


```

if anyone needs anything else please let me know and i will get it. and i have disabled ipv6 and it still didnt work.

---

