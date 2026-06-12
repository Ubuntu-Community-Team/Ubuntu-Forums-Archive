---
title: "Network card - weird pulsing??"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by davidallan on 2007-12-12
Wounder if anyone can shed some light in to why my network monitor (in sys mon) shows my traffic download (havent tried upload) pulsing. ie. going up and down. I noticed while downloading updates so I thought it could be the remote server. tried downloading a large file and it does the same! 

I hope understand my term pulsing (up and down) it seems to do it in 1-2sec intervals. tried on my other pc and its fine.

oh the network driver its using is e1000

Any help appreciated. Cheers.

---

### Post by davidallan on 2007-12-12
anyone?????

---

### Post by davidallan on 2007-12-12
Here's my settings if anyone can help me? :confused:


dna@dnahome:~$ sudo ethtool eth0
[sudo] password for dna:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
dna@dnahome:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:8a:e3:f4
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-0 ip=192.168.0.4 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
dna@dnahome:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:D1:8A:E3:F4  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe8a:e3f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3360011 (3.2 MB)  TX bytes:16348858 (15.5 MB)
          Base address:0x30c0 Memory:d3200000-d3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by davidallan on 2007-12-13
bttt

---

### Post by freshinstall on 2007-12-14
Im having the same problem with the e100 driver on a fresh install of Gutsy.

At wits end.  Have disabled ipv6, tried the openDNS, reinstalled libc6, and used the tweaks in the sysctl.conf file.

Nothing seems to affect this.  I have disabled DHCP and used a manual config same problem.
Downloads start fine then go down to 3000 B/sec then after a little while go back up then go back down.

IM disconnects although network manager does not disconnect, IM gets connection resets.  I have seen this described as pulsing or bouncing.  I would suspect the driver but others are having this problem with different drivers on fresh installs, with wired drivers.

I would appreciate any help but pls dont repeat the ipv6, openDNS, sysctl, libc6 tweaks as I have been over them a thousand times in other threads.

Also the firefox tweaks have nothing to do with this since this is happening through update manager or any downloads.

---

### Post by webjames on 2008-02-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/194832](https://bugs.launchpad.net/ubuntu/+bug/194832) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, i am also experiancing the same issues of slow gigabit speeds and the pulsing, look at my thread:
[http://ubuntuforums.org/showthread.php?p=4383724](http://ubuntuforums.org/showthread.php?p=4383724)
and my bug report:
[https://bugs.launchpad.net/ubuntu/+bug/194832](https://bugs.launchpad.net/ubuntu/+bug/194832)

---

### Post by Alajjana on 2008-03-13
> **davidallan said:**
> Wounder if anyone can shed some light in to why my network monitor (in sys mon) shows my traffic download (havent tried upload) pulsing. ie. going up and down. I noticed while downloading updates so I thought it could be the remote server. tried downloading a large file and it does the same! 

I hope understand my term pulsing (up and down) it seems to do it in 1-2sec intervals. tried on my other pc and its fine.

oh the network driver its using is e1000

Any help appreciated. Cheers.


I am using the same NIC card ( on an Intel dg33fb mb) and i am having the exact same problem. 

My thread: [http://ubuntuforums.org/showthread.php?t=718131](http://ubuntuforums.org/showthread.php?t=718131)

---

