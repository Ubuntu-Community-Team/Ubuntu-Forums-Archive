---
title: "Disabled ipv6, and internet still slow"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by a1programmer on 2008-10-08
I have disabled ipv6 in /etc/modprobe.d/aliases, and blacklisted it as suggested by others in /etc/modprobe.d/blacklist , but my internet connections are still slow.

I don't know how to tell if ipv6 is actually disabled, and if it is, I don't know where to start next...  

Ubuntu detected my wireless card, and I have 70% signal.

I am not new to linux, but this is the first time I've decided to use it as my primary OS.  

=== More Info ===

derrick@derrick-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8d:91:b9:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:91:b9:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bI believe upytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.2 KB)  TX bytes:1300 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:1b:ba:07  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12844975 (12.2 MB)  TX bytes:1578757 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-1B-BA-07-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






derrick@derrick-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


and finally...

derrick@derrick-desktop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.205.103) 56(84) bytes of data.
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=1 ttl=244 time=108 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=2 ttl=244 time=57.6 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=3 ttl=244 time=54.8 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=4 ttl=243 time=55.1 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=5 ttl=244 time=58.0 ms
64 bytes from qb-in-f103.google.com (72.14.205.103): icmp_seq=6 ttl=243 time=66.9 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5002ms
rtt min/avg/max/mdev = 54.829/66.892/108.745/19.143 ms

---

### Post by darco on 2008-10-08
run this command to determine if in fact ip6 is disabled..

```
ip a | grep inet6
```

there should be no output.
 

darco

---

### Post by willca on 2008-10-09
Append this to the end of your /etc/sysctl.conf

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


Then sudo sysclt -p

---

### Post by a1programmer on 2008-10-09
@Darco, correct... there was no output.


@willca, I appended that to the end, ran the command, and it printed the config.

Do I need to reboot after that? 

Also, and this may give more info. When I ping my router, while I am attempting to browse the web, the timeout keeps climbing... 

```
derrick@derrick-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.75 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.42 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.43 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=3.70 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.42 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.44 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=3.64 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=143 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=2.43 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=2.42 ms
 [ started browsing ]
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=1418 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=1779 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=3662 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=4016 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=4026 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=4400 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=4546 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=4164 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=4007 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=4640 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=6464 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=6232 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=6595 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=6635 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=7033 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=6710 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=6680 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=6871 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=6812 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=6235 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=5533 ms


```

---

### Post by darco on 2008-10-09
I think this is more of the same from willca

[http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

this url has alot of good info:
[http://fasterdata.es.net/TCP-tuning//linux.html](http://fasterdata.es.net/TCP-tuning//linux.html)

what wl card is this?

darco

p.s. oh and the command above is sudo sysctl -p  not sudo sysclt -p

---

### Post by a1programmer on 2008-10-10
> **darco said:**
> I think this is more of the same from willca

[http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

this url has alot of good info:
[http://fasterdata.es.net/TCP-tuning//linux.html](http://fasterdata.es.net/TCP-tuning//linux.html)

what wl card is this?

darco

p.s. oh and the command above is sudo sysctl -p  not sysclt -p

Yep, I did a sudo.  It didn't seem to make any difference.

I have a somewhat cheap wireless card that I bought from newegg. How do I tell what chipset easily ?

---

### Post by hyper_ch on 2008-10-10
are you on wireless? If so, what does
```

iwconfig

```
return?

---

### Post by a1programmer on 2008-10-10
Yes, it's wireless... I'm at work, but will do that as soon as I get home.

From my very first post, you can see wlan0 from the 'ifconfig -a'.

---

### Post by hyper_ch on 2008-10-10
I'm asking for something different ;)

---

### Post by a1programmer on 2008-10-11
results of iwconfig

```
root@derrick-desktop:/home/derrick# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Derrick"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:B5:28:91:DE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:B613-B4AC-DD5B-3CCB-FEC8-E890-D0C5-A68D-7AAB-0A3B-BC64-BAC6-FA5A-CA00-4F0A-0863 [3]
          Link Quality=49/100  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by hyper_ch on 2008-10-12
I think that's the problem
```

Bit Rate=1 Mb/s 

```

It gets set to me also always to 1Mb/s...

run
```

sudo /etc/init.d/networking restart
sudo iwconfig wlan0 rate 54M

```
I assume, you have a 54M wireless card and access point.

---

### Post by a1programmer on 2008-10-12
> **hyper_ch said:**
> I think that's the problem
```

Bit Rate=1 Mb/s 

```

It gets set to me also always to 1Mb/s...

run
```

sudo /etc/init.d/networking restart
sudo iwconfig wlan0 rate 54M

```
I assume, you have a 54M wireless card and access point.

It looks like that was the problem... Thanks!!!

---

### Post by hyper_ch on 2008-10-13
if it happens to be resetted to 1 Mb/s regurarly, please tell here that you got the same problem:  [https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

---

### Post by a1programmer on 2008-10-13
Yep, it seems to be reset every time I reboot...  I was going to set the command to set it to 54M in my profile. Is there a better place I should set it?

Thanks.

---

### Post by hyper_ch on 2008-10-13
I haven't got a solution yet for it... did you append the bug report?

---

