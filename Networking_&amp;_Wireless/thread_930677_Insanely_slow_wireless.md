---
title: "Insanely slow wireless"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by kano on 2008-09-26
Hi, I'm trying to set up Ubuntu 8.04 on my girlfriends Sony Vaio NR330E and have been having alot of trouble getting the wireless working.

I managed to get the Atheros 5007EG wireless device working by using the modified madwifi-hal. I can connect to my wireless network and it gets an ip, etc.

Now the problem I'm having is- The connection is ridiculous slow. I have my own laptop (Dell M1530/ndiswrapper) running ArchLinux that connects just fine and has no problem, so it's not the AP. The wired connection also works perfect on the Sony.

With WEP enabled on the router, it's unusably slow. Shutting off WEP improves it, but it's still slow.

Pinging router w/ WEP:
```

PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=10550 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=9879 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=11029 ms
64 bytes from 10.0.0.1: icmp_seq=4 ttl=64 time=11389 ms
64 bytes from 10.0.0.1: icmp_seq=5 ttl=64 time=10979 ms
64 bytes from 10.0.0.1: icmp_seq=6 ttl=64 time=11049 ms
64 bytes from 10.0.0.1: icmp_seq=7 ttl=64 time=10499 ms

--- 10.0.0.1 ping statistics ---
13 packets transmitted, 7 received, 46% packet loss, time 17029ms
rtt min/avg/max/mdev = 9879.343/10768.287/11389.800/461.083 ms, pipe 10

```

```

erin@tigerwigerbutt:~$ ping -c4 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=6689 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=6803 ms (DUP!)
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=5859 ms
64 bytes from 10.0.0.1: icmp_seq=4 ttl=64 time=5740 ms

--- 10.0.0.1 ping statistics ---
4 packets transmitted, 3 received, +1 duplicates, 25% packet loss, time 3008ms
rtt min/avg/max/mdev = 5740.046/6273.062/6803.847/476.993 ms, pipe 3


```

I'm pretty good at figuring things out, but this one just baffles me :confused:

Other info:
iwconfig
```

ath0      IEEE 802.11g  ESSID:"PenguinWireless"  Nickname:"PenguinWireless"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:96:25:98   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:73  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```

ath0      Link encap:Ethernet  HWaddr 00:1d:d9:df:11:e4  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fedf:11e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3576040 (3.4 MB)  TX bytes:229111 (223.7 KB)

```
lshw
```

           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wifi0
                version: 01
                serial: 00:1d:d9:df:11:e4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=10.0.0.5 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by shanix on 2008-09-26
Were you happen to use the following as reference?
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Perhaps the pci ID on the card will be useful and a sime of wireshark captured file to see what might be causing this.

---

### Post by kano on 2008-09-26
> **shanix said:**
> Were you happen to use the following as reference?
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Perhaps the pci ID on the card will be useful and a sime of wireshark captured file to see what might be causing this.

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192), when I tried the ubuntugeek instructions I got a tarball with a README telling me to see that. I compiled and installed, and after a reboot it detected the card.

Now that i've been playing with it more, it seems intermittent :s It'll be fine then 90% of the packets will drop, wait a couple minutes and it's fine again :/

---

### Post by shanix on 2008-09-26
Would it be possible to test this on another wireless network? Might not be the system issue.... :-/

---

### Post by kano on 2008-09-26
I can test with built-in wireless on the router, the wireless I normally use is a dedicated AP that is connected to the router via ethernet.

It works perfect on my laptop and another XP laptop though :/ 

I was playing around with wireshark and it's getting a decent amount of duplicate packets when it's working. When the internet stops working, 10.0.0.5 (the sony laptop) asks who 10.0.0.1 (the router) is over and over about 20-30 times before getting blasted by 20-30 responses from the router instantly and it starts working again.

---

### Post by kano on 2008-09-26
edit: I upgraded to Intrepid Ibex and now everything is working great. :) Guess it was something with network-manager or something.

---

