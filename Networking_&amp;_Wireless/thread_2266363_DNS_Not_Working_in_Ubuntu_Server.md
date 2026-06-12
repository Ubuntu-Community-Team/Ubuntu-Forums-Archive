---
title: "DNS Not Working in Ubuntu Server"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by alasdair3 on 2015-02-22
I'm running ubuntu server 14 and have a wired connection to my router. I have not previously been experiencing any issues.

For no apparant reason today my apt-get could not resolve addresses. When I looked further into the problem I found that I could ping ip addresses but not domain names so I suspected a DNS problem. Based on searching other similar issues I edited my /etc/resolv.conf file to contain:

nameserver 8.8.8.8
nameserver 8.8.4.4

but it still doesn't work.

I'm a bit lost now as I don't know what to try next.

If anyone can give me some advice on what to do next it would be very much appreciated. Hopefully the below info is useful.

Many thanks in advance for your help.

```


$ ping google.com
ping: unknown host google.com

$ ping 216.58.208.78
PING 216.58.208.78 (216.58.208.78) 56(84) bytes of data.
64 bytes from 216.58.208.78: icmp_seq=1 ttl=58 time=7.16 ms
64 bytes from 216.58.208.78: icmp_seq=2 ttl=58 time=7.32 ms
64 bytes from 216.58.208.78: icmp_seq=3 ttl=58 time=6.74 ms
64 bytes from 216.58.208.78: icmp_seq=4 ttl=58 time=6.94 ms
^C
--- 216.58.208.78 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 6.748/7.043/7.321/0.239 ms

$ cat /etc/resolv.conf

nameserver 90.207.238.97
nameserver 8.8.8.8
nameserver 8.8.4.4

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
iface p3p1 inet dhcp

$ ifconfig -a
em1       Link encap:Ethernet  HWaddr fc:aa:14:21:04:a6  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7e00000-f7e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:590202 (590.2 KB)  TX bytes:590202 (590.2 KB)

p3p1      Link encap:Ethernet  HWaddr fc:aa:14:21:04:a4  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fe21:4a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr a0:a8:cd:c5:ad:f5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ lshw -class network

  *-network DISABLED      
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: em1
       version: 00
       serial: fc:aa:14:21:04:a6
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7e00000-f7e1ffff memory:f7e3c000-f7e3cfff ioport:f080(size=32)
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: p3p1
       version: 10
       serial: fc:aa:14:21:04:a4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:50 memory:f7d00000-f7d3ffff ioport:e000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 73
       serial: a0:a8:cd:c5:ad:f5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-44-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f7c00000-f7c01fff


```

---

### Post by steeldriver on 2015-02-22
AFAIK the default installation of Ubuntu Server 14.04 uses resolvconf (dynamic resolver) however you appear to have a fixed /etc/resolv.conf file. Is resolvconf still running? installed?

```

service resolvconf status

dpkg -l resolvconf

```

---

### Post by alasdair3 on 2015-02-22
So while trying to fix this problem I followed some instructions for removing resolvconf with the intention of reinstalling it. Foolishly I forgot that apt-get wasn't working so I couldn't reinstall it afterwards.

So in short - no, resolvconf is not installed.

---

### Post by steeldriver on 2015-02-22
Have you tried simply removing (or commenting out) the 90.207.238.97 nameserver? I can't get a timely response from it. Then restart the networking service (or reboot, to be certain).

---

### Post by alasdair3 on 2015-02-22
I removed the 90.207.238.97 nameserver and rebooted but still can't ping google.com. I tried had tried putting that DNS server there because it's the one my router is currently set to use. Other computers connected to my network are working fine.

---

### Post by steeldriver on 2015-02-22
Hmm... that's a bit of a puzzle then. What does

```

dig google.com

```

say?  that should at least identify which nameserver it is attempting to contact. BTW does your router provide DNS service? if so, DHCP may be pushing that - I'm no certain which takes precedence

---

### Post by alasdair3 on 2015-02-22
Not sure what the output means - hopefully it makes sense to you.
```


$ dig google.com

; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34767
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.            IN    A

;; ANSWER SECTION:
google.com.        114    IN    A    216.58.208.46

;; Query time: 6 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Feb 22 16:49:50 GMT 2015
;; MSG SIZE  rcvd: 44
```

I think the router was offering the DNS service. In the router settings it's got a section saying it's using the DNS server 90.207.238.97. 

When I had resolvconf installed my resolv.conf file used to have a nameserver entry pointing at my router IP address. I've tried having that in there but it doens't make a difference. Besides, it seems odd that system can't use the public servers. Even stranger that it used to work fine and this issue whole came out of the blue having made no changes to the system.

Thanks for your ongoing help.

---

### Post by steeldriver on 2015-02-22
Well unless I'm misreading it, it says it **is **using your router's DNS server [ SERVER: 192.168.0.1#53(192.168.0.1) ] and **is **successfully resolving the name [ google.com.        114    IN    A    216.58.208.46 ]

So I'm puzzled why ping says it can't resolve it

---

### Post by alasdair3 on 2015-02-22
I don't understand why it's using the router for DNS when that's not what's specified in /etc/resolv.conf.

I've just tried it again and the system definitely can't ping and apt-get doesn't resolve either:

```


$ dig google.com

; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4917
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.            IN    A

;; ANSWER SECTION:
google.com.        127    IN    A    216.58.210.14

;; Query time: 7 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Feb 22 17:38:28 GMT 2015
;; MSG SIZE  rcvd: 44


$ ping google.com
ping: unknown host google.com


$ sudo apt-get update
Err http://gb.archive.ubuntu.com trusty InRelease
  
Err http://gb.archive.ubuntu.com trusty-updates InRelease
  
Err http://gb.archive.ubuntu.com trusty-backports InRelease
  
Err http://security.ubuntu.com trusty-security InRelease
  
Err http://plex.r.worldssl.net lucid InRelease
  
Err http://gb.archive.ubuntu.com trusty Release.gpg
  Could not resolve 'gb.archive.ubuntu.com'
Err http://gb.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'gb.archive.ubuntu.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://plex.r.worldssl.net lucid Release.gpg
  Could not resolve 'plex.r.worldssl.net'
Err http://gb.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'gb.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/InRelease  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'gb.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/Release.gpg  Could not resolve 'plex.r.worldssl.net'

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

Is there anything else I could try or any other issue that could be causing this if this isn't a DNS issue?

---

### Post by alasdair3 on 2015-02-23
I solved this eventually, please see:  [http://ubuntuforums.org/showthread.php?t=2266459](http://ubuntuforums.org/showthread.php?t=2266459)

---

