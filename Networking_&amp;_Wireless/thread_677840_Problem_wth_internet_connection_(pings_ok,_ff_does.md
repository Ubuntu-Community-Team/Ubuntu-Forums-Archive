---
title: "Problem wth internet connection (pings ok, ff doesn't work)"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by gumispl on 2008-01-25
Good morning,

I have problem with configuring internet connection on fresh installed Ubuntu 7.10.
Ubuntu detected my ethernet card and get settings from DHCP server without problem.
(ip 192.168.0.8, gateway ip 192.168.0.1, subnet mask 255.255.255.0 and dns's are aright)
Local server is running under Debian Linux, all 10 pcs connected to it works ok (all are running win xp)

I can ping for ex. google.com or yahoo.com,  but i can't browse in FF. In status bar it says me for ex.: "connecting to google.com, connected to google.com, waiting for responses.." and nothing to see.
I can surf into my local server (ip 192.168.0.1), but i can't browse to my modem (192.168.1.1, it's on the different ethernet card in server).
Exceptionally, i can surf to the mozilla.org website, and while trying to surf microsoft.com firefox downloads favicon... on the other small part of pages i can see title tag...
What's wrong?

I have the same problem on other Linux distributions as Kubuntu, Backtrack. I also tried it on my laptop but there is the same issue. In turn in Knoppix 3.3 (based on Kernel 2.4) internet works ok.

I saw similar problem to my, described here: [http://ohioloco.ubuntuforums.org/showthread.php?t=656661](http://ohioloco.ubuntuforums.org/showthread.php?t=656661) but blacklisting ipv6 doesn't help :( 

Thanks in advance.

P.S. Sorry for my English, i know it's bad but I'm still learning it. I hope You understand what i mean :)

---

### Post by Mithrilhall on 2008-01-25
Do you have a firewall running?

Could you do a traceroute to google and post the results?

---

### Post by gumispl on 2008-01-25
1) It's clear install of Ubuntu, there is no any rules in iptables.
It's only firewall on debian server, i think it's ok because all win xp clients can browse pages.

2)
traceroute google:
```

~#traceroute google.com
traceroute: Warning: google.com has multiple addresses; using 64.233.167.99
traceroute to google.com (64.233.167.99), 30 hops max, 38 byte packets
 1  192.168.0.1 (192.168.0.1)  2.375 ms  0.191 ms  0.123 ms
 2  * * *
 3  bras-waw-dbp-r01.net.ipartners.pl (157.25.255.227)  20.627 ms  19.885 ms  19.922 ms
 4  157.25.4.121 (157.25.4.121)  20.693 ms  19.905 ms  18.903 ms
 5  * taro-wawa2-so-4-0-0.net.ipartners.pl (157.25.4.61)  23.670 ms *
 6  gsr1-pos9-0.net.ipartners.pl (157.25.3.101)  29.431 ms  27.901 ms  29.940 ms
 7  war-b3-link.telia.net (213.248.99.157)  20.120 ms  19.984 ms  20.597 ms
 8  hbg-bb1-pos6-2-0.telia.net (213.248.96.1)  36.434 ms  35.946 ms  35.978 ms
 9  ldn-bb1-link.telia.net (80.91.250.221)  56.499 ms  56.990 ms ldn-bb1-link.telia.net (80.91.254.217)  66.044 ms
10  nyk-bb1-link.telia.net (80.91.249.249)  123.025 ms  119.914 ms  122.007 ms
11  chi-bb1-pos6-0-0-0.telia.net (213.248.80.153)  143.997 ms  144.595 ms  141.948 ms
12  google-118691-chi-bb1.c.telia.net (213.248.84.90)  146.044 ms  141.939 ms  143.968 ms
13  216.239.48.154 (216.239.48.154)  144.039 ms 209.85.250.237 (209.85.250.237)  144.049 ms  143.665 ms
14  66.249.95.120 (66.249.95.120)  145.999 ms  146.336 ms 72.14.232.53 (72.14.232.53)  146.620 ms
15  64.233.175.26 (64.233.175.26)  158.117 ms 72.14.232.74 (72.14.232.74)  144.888 ms 64.233.175.42 (64.233.175.42)  157.077 ms
16  py-in-f99.google.com (64.233.167.99)  143.043 ms  146.620 ms  154.986 ms

```

traceroute mozilla.org (working page)
```

~#traceroute mozilla.org
traceroute to mozilla.org (63.245.209.11), 30 hops max, 38 byte packets
 1  192.168.0.1 (192.168.0.1)  0.266 ms  7.590 ms  7.813 ms
 2  * * *
 3  bras-waw-dbp-r01.net.ipartners.pl (157.25.255.227)  27.936 ms  20.747 ms  19.963 ms
 4  157.25.4.121 (157.25.4.121)  23.866 ms  24.043 ms  19.771 ms
 5  taro-wawa2-so-4-0-0.net.ipartners.pl (157.25.4.61)  21.886 ms  19.782 ms  20.676 ms
 6  plwaw3-so-4-0-0-0.net.ipartners.pl (157.25.3.162)  22.112 ms  19.844 ms  19.980 ms
 7  fra-tr1-p0-1-1.gtsce.net (195.39.208.69)  45.854 ms  51.847 ms  43.464 ms
 8  decix1.mpr1.fra1.de.above.net (80.81.192.226)  149.603 ms  147.995 ms  146.966 ms
 9  po60.mpr2.fra1.de.above.net (64.125.23.233)  151.008 ms  144.782 ms  148.925 ms
10  so-3-0-0.mpr3.ams1.nl.above.net (64.125.23.254)  129.999 ms so-3-1-0.mpr3.ams1.nl.above.net (64.125.23.250)  133.279 ms so-3-0-0.mpr3.ams1.nl.above.net (64.125.23.254)  130.048 ms
11  so-2-1-0.mpr1.lga5.us.above.net (64.125.27.185)  147.023 ms  143.144 ms  145.990 ms
12  so-2-1-0.mpr1.sjc2.above.net (64.125.26.229)  256.913 ms  216.239 ms  223.609 ms
13  GW-GNI.above.net (64.124.73.34)  202.038 ms  204.803 ms  200.042 ms
14  core-01.ge-5-13.sfo1.gni.com (64.127.96.30)  205.033 ms  198.930 ms  200.930 ms
15  core-01.ge-1-1.sjc1.gni.com (64.127.96.57)  207.452 ms  202.854 ms  209.008 ms
16  69.80.192.94 (69.80.192.94)  218.971 ms  225.506 ms  218.965 ms
17  v8.core1.sj.mozilla.com (63.245.208.49)  226.004 ms  225.921 ms  220.949 ms
18  moz.org01.nslb.sj.mozilla.com (63.245.209.11)  212.008 ms  206.911 ms  213.006 ms

```

route
```

~#route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
loopback        *               255.0.0.0       U     0      0        0 lo
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

ifconfig
```

~#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:6C:EC:9A:9A
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:224938 (219.6 KiB)  TX bytes:56292 (54.9 KiB)
          Interrupt:16 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

ping google :):):)
```

~#ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=231 time=170 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=231 time=160 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=231 time=160 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=231 time=164 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 160.273/163.938/170.996/4.396 ms

```

EDT:
tcpdump (from ubuntu, not from server)
```

~#tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
16:55:59.276799 IP 192.168.0.8.36598 > py-in-f99.google.com.http: S 3730758444:3730758444(0) win 5840 <mss 1460,sackOK,timestamp 664117 0,nop,wscale 6>
16:55:59.288526 IP 192.168.0.8.32770 > cns1.ikp.pl.domain: 564+ PTR? 99.167.233.64.in-addr.arpa. (44)
16:55:59.310730 IP cns1.ikp.pl.domain > 192.168.0.8.32770: 564 1/4/4 (214)
16:55:59.311027 IP 192.168.0.8.32770 > cns1.ikp.pl.domain: 53333+ PTR? 22.0.168.192.in-addr.arpa. (43)
16:55:59.332713 IP cns1.ikp.pl.domain > 192.168.0.8.32770: 53333 NXDomain* 0/1/0 (93)
16:55:59.333317 IP 192.168.0.8.32770 > cns1.ikp.pl.domain: 41696+ PTR? 244.168.8.217.in-addr.arpa. (44)
16:55:59.354711 IP cns1.ikp.pl.domain > 192.168.0.8.32770: 41696 1/3/4 (199)
16:55:59.437495 IP py-in-f99.google.com.http > 192.168.0.8.36598: S 3984572161:3984572161(0) ack 3730758445 win 5672 <mss 1430,sackOK,timestamp 3232556578 664117,nop,wscale 6>
16:55:59.437546 IP 192.168.0.8.36598 > py-in-f99.google.com.http: . ack 1 win 92 <nop,nop,timestamp 664157 3232556578>
16:55:59.438136 IP 192.168.0.8.36598 > py-in-f99.google.com.http: P 1:397(396) ack 1 win 92 <nop,nop,timestamp 664157 3232556578>
16:55:59.606826 IP py-in-f99.google.com.http > 192.168.0.8.36598: . ack 397 win 106 <nop,nop,timestamp 3232556750 664157> 

```

wget
```

~# wget -O- "http://google.com"
--17:01:29--  http://google.com/
           => `-'
Resolving google.com... 64.233.167.99, 72.14.207.99, 64.233.187.99
Connecting to google.com|64.233.167.99|:80... connected.
HTTP request sent, awaiting response...

```

---

### Post by Mithrilhall on 2008-01-25
Ok..so every computer you have is passing through your Debian server, correct? Try connecting the Ubuntu computer directly to the internet; bypass the Debian server and the router if at all possible.

If you do that can you get online?

---

### Post by gumispl on 2008-01-26
Ok, i connected laptop with Ubuntu (booted as live cd) directly to modem (via ethernet cable). Unfortunately, the same problem is occuring.

EDT:
List of pages which i can browse:
mozilla.org, proxy.org, who.is, esda.wu-wien.ac.at, onebigproxy.com
and list of pages where i can read title tag:
cnn,com, microsoft.com, tvp.pl

I can browse some specific pages, it's funny, isn't?

---

### Post by gumispl on 2008-01-27
Hm.. I found this in user.log:
```

Jan 27 22:23:53 krzysiek-desktop dhcdbd: Started up.
Jan 27 22:23:56 krzysiek-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jan 27 22:23:58 krzysiek-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Jan 27 22:23:58 krzysiek-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jan 27 22:23:58 krzysiek-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

```

It's appearing always when i start computer, what does it mean?

---

### Post by gumispl on 2008-02-07
Sorry for refreshing...

But problem is still occuring. I have installed squid on my debian server so i can browse pages and use synaptic.  

But i must have a direct access to internet...

---

### Post by blingo on 2008-02-07
Check if this is similar to your problem.
[http://ubuntuforums.org/showthread.php?t=643058](http://ubuntuforums.org/showthread.php?t=643058)

---

### Post by gumispl on 2008-02-08
**SOLVED**

I must did: 
```
sudo sh -c "echo 0 > /proc/sys/net/ipv4/tcp_window_scaling"
```

And now all works.

Thanks to erUSUL from #ubuntu who said to use this command.

---

