---
title: "Slow browsing..."
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by heri0n on 2006-12-16
I'm using Firefox 1.5.0.8 on Dapper
and my browsing seems pretty slow now.
It may have been after one of the updates installed a new kernel... but I'm not sure.
Browsing is fast on Windows.
And downloading is fast on linux too, just browsing is slow.
I did try removing the ipv6 stuff 
by adding this to /etc/modprobe.d/aliases
#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

rebooted.. no noticable speedups...
I have tried installing Konquerer and browsing with that... same

dig google.com gives me a 9ms query time

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:81:A7:D0
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe81:a7d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1591824 (1.5 MiB)  TX bytes:481523 (470.2 KiB)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


hmmm wait that doesnt look right... what is sit0? could that be the cause of my problems?

--Edit--
actually right after i saw this... i added 
alias sit0 off
to my aliases
and i also added blacklist ipv6 in my blacklist file
that didnt seem to change anything
it did get rid of the sit0 entry though..
--Edit--
anyways continuing with diagnostics

host google.com gave me a pretty fast response

cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       heri0n-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

should i remove the ipv6 stuff?


traceroute google.com
traceroute: Warning: google.com has multiple addresses; using 64.233.187.99
traceroute to google.com (64.233.187.99), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.773 ms  0.641 ms  0.653 ms
 2  cn-rtuwp-uwpr3net.uwaterloo.ca (129.97.248.1)  3.156 ms  3.502 ms  3.614 ms
 3  cn-rtres-resnet.uwaterloo.ca (129.97.191.1)  3.275 ms  3.972 ms  2.709 ms
 4  129.97.1.193 (129.97.1.193)  4.124 ms  3.955 ms  3.559 ms
 5  cn-rtext.uwaterloo.ca (129.97.10.3)  4.130 ms  4.334 ms  3.138 ms
 6  * g0-9.na21.b011027-0.yyz02.atlas.cogentco.com (38.99.202.213)  7.136 ms *
 7  v3492.mpd01.yyz01.atlas.cogentco.com (154.54.5.81)  6.822 ms  207.350 ms  206.963 ms
 8  g2-0-0-3490.core01.yyz01.atlas.cogentco.com (154.54.5.73)  7.101 ms  7.485 ms  6.211 ms
 9  p13-0.core02.ord01.atlas.cogentco.com (66.28.4.213)  25.178 ms  61.083 ms  23.555 ms
10  te3-3.mpd01.ord01.atlas.cogentco.com (154.54.1.178)  23.169 ms  20.180 ms  20.357 ms
11  v3499.mpd01.ord03.atlas.cogentco.com (154.54.5.10)  21.498 ms  22.795 ms  22.900 ms
12  google.ord03.atlas.cogentco.com (154.54.11.186)  20.530 ms  22.306 ms  20.446 ms
13  66.249.95.253 (66.249.95.253)  22.372 ms  20.872 ms  26.468 ms
14  72.14.236.26 (72.14.236.26)  41.035 ms  45.768 ms 66.249.95.245 (66.249.95.245)  22.286 ms
15  64.233.175.99 (64.233.175.99)  41.689 ms  41.758 ms  43.103 ms
16  72.14.239.21 (72.14.239.21)  43.683 ms  44.006 ms  42.254 ms
17  216.239.49.226 (216.239.49.226)  57.004 ms 64.233.187.99 (64.233.187.99)  42.260 ms  42.072 ms

anymore info needed?
please help...

---

### Post by spd106 on 2006-12-16
Have you tried turning off ipv6 in firefox? Enter about:config into the location bar and toggle the network.dns.disableIPv6 setting to true

Also try [http://www.ubuntuforums.org/showpost.php?p=1894777&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1894777&postcount=8)

---

### Post by heri0n on 2006-12-17
it still seems pretty slow..
it seems to take the most time when it says
Looking up <website> ...

---

### Post by heri0n on 2006-12-17
bump..

---

### Post by heri0n on 2006-12-17
ok looks like i figured it out..
i guess linux wasnt figuring out which nameserver was fastest to use..

#search uwaterloo.ca
#nameserver 129.97.191.20
nameserver 129.97.191.15

ya i commented out the first two lines from /etc/resolve.conf
and now its much faster!!
no thanks to you guys :P

---

