---
title: "I keep losing wireless signal.  Any idea why?"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by MrCashMan on 2008-09-23
Hello all,

I installed Ubuntu 8.04 on my desktop machine and have thus far been VERY pleased. I am however having a strange problem with my wireless connection. It detects my card just fine, and I am able to get on my wireless network no problem. However, it seems that when I start downloading above a certain threshold of bandwidth, my wireless connection dies, and I'm unable to get it back unless I restart the computer. A friend told me to try this command:

sudo /etc/init.d/networking restart

But it doesn't help. Here is an output of something that I saw in another thread about someone else having problems, so I ran the same command to see if the info might be relevant to my problem.  This is a Linksys WMP11 wireless card.

lloyd@lloyd-desktop:~$ sudo lshw -C network
[sudo] password for lloyd:
*-network
description: Wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: b
bus info: pci@0000:02:0b.0
logical name: wifi0
version: 01
serial: 00:06:25:a7:71:89
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical wireless ethernet physical
configuration: broadcast=yes driver=hostap firmware=1.4.2 ip=192.168.1.3 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b

Any help would be greatly appreciated! 

Regards,
Lloyd

---

### Post by MrCashMan on 2008-09-24
?

---

### Post by willca on 2008-09-24
similar problem i had...maybe this will work for you regarding some limits set in your tcp stack preventing you from passing more traffic.

Edit your /etc/sysctl.conf

Add the following lines at the end.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1


Save and sudo /etc/init.d/networking restart

---

### Post by MrCashMan on 2008-09-24
Thank you SO MUCH!  I do believe that this has done the trick.  I've had Azureus up and running for about 10 minutes at over 400 kB/s and so far my connection is handling it.  I'm going to let it run for a while longer before I belive it to be final, but I think you have solved my problem.  Again, thank you!

---

### Post by MrCashMan on 2008-09-24
ugh, looks like i jinx'd myself.  Not 2 minutes after I posted that it fixed it, my connection died again.  I may just have to get a new card.  This card is from 2003, and I could probably use an n compatible card anyway.  Thanks for trying, though.

---

### Post by Crafty Kisses on 2008-09-24
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```

I also want to see the results of this command:
```
lshw -C network
```

I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

I see that you have solved your issues, but this may be a possibility or a factor of the problem. I had the exact same issue as you, and it turned out all it was, was severe packet loss, and I did some commands and moved some things around and it works like a charm.

---

### Post by lestatius on 2009-07-21
> **willca said:**
> similar problem i had...maybe this will work for you regarding some limits set in your tcp stack preventing you from passing more traffic.

Edit your /etc/sysctl.conf

Add the following lines at the end.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1


Save and sudo /etc/init.d/networking restart

I'm running on ubuntu 9.04 Desktop
I have the same problem. I tried this but it didn't work. I have a Compaq nc6320 hp laptop. here's my wireless info:

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:bc:9f:a7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.23 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

It can't be a problem that I'm too far away from my router(losing packets) cuz I'm less then 10m away from it and my main pc running on windows isn't have problems with connections.


ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:bc:9f:a7  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:febc:9fa7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18601746 (18.6 MB)  TX bytes:913811 (913.8 KB)


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"jigsawpuzzle"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:5C:1F:EA   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=78/100  Signal level:-56 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

