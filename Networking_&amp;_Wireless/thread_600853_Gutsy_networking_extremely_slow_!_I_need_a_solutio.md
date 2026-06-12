---
title: "Gutsy networking extremely slow ! I need a solution !"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-11-02
I can't believe how bad networking is in Gutsy.

My main problem right now is extremely slow upload speeds.  I am using a Broadcom wireless card.  Everything works and is more or less stable, but its ssslllloooowwww.  I am sending emails with 4MB attachments and it takes FOREVER.  (30 minutes !)

What is the sure fire way to fix this ?

---

### Post by Lambert on 2007-11-03
depends where the trouble is. 

Post output of

```

sudo iwconfig

sudo ifconfig

```

also I read a post where there is a confirmed bug about networking in gutsy and network speeds. I haven't seen the actual bug report but this could be the problem also.

---

### Post by elmerfud on 2007-11-03
sudo iwconfig

lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:D0:53:8A
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:4B:57:EA:5B
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe57:ea5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:109155774 (104.0 MB)  TX bytes:40538484 (38.6 MB)
          Interrupt:22 Memory:d2004000-d2006000

eth2      Link encap:Ethernet  HWaddr 00:C0:9F:43:6C:DA
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1338 (1.3 KB)  TX bytes:1338 (1.3 KB)

---

### Post by Lambert on 2007-11-03
I see two interfaces and two different subnets.

Explain your network set up (which subnet hooks into the internet; which is just a local subnet).

Run this command and post output.

```

ip route

```

also

```

sudo ethtool eth2

```

And one last check. Install the package traceroute. You can do this from synaptic package manager or command line

```

sudo apt-get install traceroute

```

then run the command

```

traceroute www.ubuntuforums.org

```

and you can post the output of that here. This traces the path taken for traffic and shows how long it takes to each hop.

Your problem could be the confirmed bug or a very possible routing problem.

---

### Post by elmerfud on 2007-11-03
eth1 is the Broadcom wireless card
eth2 is a wired Ethernet card.  I am manually assigning it an IP.  Its not used for anything.  I could disable it without much trouble.


$ ip route
192.168.2.0/24 dev eth2  proto kernel  scope link  src 192.168.2.1
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.101
169.254.0.0/16 dev eth2  scope link  metric 1000
default via 192.168.0.1 dev eth1
default via 192.168.0.1 dev eth1  metric 100

$ sudo ethtool eth2

Settings for eth2:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: no



$ traceroute [www.ubuntuforums.org](www.ubuntuforums.org)
traceroute to [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.186), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  2.633 ms  3.075 ms  3.375 ms
 2  S010600121712035a.cg.shawcable.net (68.146.170.1)  20.547 ms  21.845 ms  23.543 ms
 3  rd1no-ge3-0-0-16.cg.shawcable.net (64.59.142.99)  18.158 ms  18.231 ms  19.134 ms
 4  rc1no-ge6-0-0.cg.shawcable.net (66.163.77.5)  19.202 ms  19.700 ms  21.204 ms
 5  rc1so-pos15-0.cg.shawcable.net (66.163.77.9)  22.435 ms  23.224 ms *
 6  rc1wh-pos3-0-0.vc.shawcable.net (66.163.77.197)  36.252 ms  26.962 ms  32.609 ms
 7  rc1wt-pos1-0-0.wa.shawcable.net (66.163.76.2)  34.295 ms  34.841 ms  35.886 ms
 8  te-3-4.car3.Seattle1.Level3.net (4.71.152.25)  36.335 ms  37.461 ms  38.117 ms
 9  ae-31-53.ebr1.Seattle1.Level3.net (4.68.105.94)  46.221 ms  47.119 ms  47.240 ms
10  ae-1-100.ebr2.Seattle1.Level3.net (4.69.132.18)  41.327 ms  42.211 ms  42.368 ms
11  ae-2.ebr2.Denver1.Level3.net (4.69.132.54)  81.283 ms *  81.531 ms
12  ae-3.ebr3.Chicago1.Level3.net (4.69.132.62)  58.093 ms  74.126 ms  70.375 ms
13  ae-68.ebr1.Chicago1.Level3.net (4.69.134.57)  81.230 ms  81.436 ms  81.280 ms
14  ae-2.ebr2.NewYork1.Level3.net (4.69.132.66)  98.211 ms  99.728 ms  99.542 ms
15  ae-72-72.csw2.NewYork1.Level3.net (4.69.134.86)  93.185 ms ae-82-82.csw3.NewYork1.Level3.net (4.69.134.90)  97.774 ms ae-92-92.csw4.NewYork1.Level3.net (4.69.134.94)  92.590 ms
16  ae-61-61.ebr1.NewYork1.Level3.net (4.69.134.65)  102.871 ms ae-71-71.ebr1.NewYork1.Level3.net (4.69.134.69)  101.506 ms ae-81-81.ebr1.NewYork1.Level3.net (4.69.134.73)  101.503 ms
17  ae-4.ebr2.London1.Level3.net (4.69.132.110)  165.494 ms  167.614 ms  171.646 ms
18  ae-1-100.ebr1.London1.Level3.net (4.69.132.117)  171.275 ms  171.343 ms  171.219 ms
19  ae-2.ebr2.London2.Level3.net (4.69.132.145)  167.993 ms  168.724 ms  164.512 ms
20  ae-26-56.car2.London2.Level3.net (4.68.117.176)  165.631 ms ae-26-54.car2.London2.Level3.net (4.68.117.112)  164.885 ms ae-26-52.car2.London2.Level3.net (4.68.117.48)  166.306 ms
21  195.50.121.2 (195.50.121.2)  164.190 ms  227.479 ms  230.190 ms
22  gw0-0-gr.canonical.com (91.189.88.10)  166.105 ms  164.240 ms  157.536 ms
23  * * *
24  * * *
25  * * *
26  * * *
27  * *

---

### Post by ybukhman on 2007-11-03
Hi,

I have a similar problem.  My internet became much slower when I switched from Feisty to Gutsy.  Judging by the Firefox status bar, it takes a lot of time to look up a web address.  Is there a way to diagnose and fix this?

---

### Post by ybukhman on 2007-11-03
> **ybukhman said:**
> Hi,

I have a similar problem.  My internet became much slower when I switched from Feisty to Gutsy.  Judging by the Firefox status bar, it takes a lot of time to look up a web address.  Is there a way to diagnose and fix this?

Looks like disabling IPv6 solved my problem. Maybe it could help some people?

There's a how-to and a discussion here: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

In short, here's what I had to do:

Create file named bad_list in /etc/modprobe.d containing this line:
Code:

alias net-pf-10 off

Now reboot and voila, no IPv6 on your system!

To check IPv6 state open terminal and execute:
Code:

ip a | grep inet6

If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.

---

### Post by elmerfud on 2007-11-05
I disabled ipv6 and my Internet connection is twice as fast.  What a difference !  

Its a crying shame that I suffered with slow Internet for the last month or so.  Why the heck is Gutsy shipping with this installed ?

For the record, creating a bad_list file didn't help.  ip -a still showed inet6 was still running.  Are you sure you didn't mean blacklist instead of bad_list ?  

I also tried editing the aliases file.  No joy.

What did work was editing /etc/modprobe.d.  I added blacklist ipv6 and rebooted and ip -a shows no traces of inet6.

Yippee... I have decent Internet speed again !

---

### Post by Can+~ on 2007-11-05
Linux had IPv6 since 1996. :confused:

[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

---

### Post by elmerfud on 2007-11-14
There is still something wrong with Gutsy networking.  

I was downloading some files from the Internet and I can't even browse while that is going on.  This is ridiculous.  I am going back to Fedora when I get a chance.

---

