---
title: "Can anyone shed some light on this static ip config"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by houserparker on 2009-11-05
Ive followed all all the instructions on configuring a staic ip but there all based around the fact that the primary network interface is listed as eth0 but when i type ifconfig it states that mine is eth2. I have applied the following to /etc/network/interfaces but on restart i can no longer see any networks.

Can anyone shed some light on what i may be doing wrong.

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

ben@ben-laptop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:24:2c:15:5b:bc  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe15:5bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9013 errors:0 dropped:0 overruns:0 frame:5926
          TX packets:6913 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10284958 (10.2 MB)  TX bytes:825670 (825.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9238 (9.2 KB)  TX bytes:9238 (9.2 KB)

---

### Post by kixome on 2009-11-05
do you have more than one network interface?

---

### Post by kixome on 2009-11-05
IN /ETC/NETWORK/INTERFACES change eth0 to eth2

---

### Post by houserparker on 2009-11-05
Only wired and wireless card, wireless card being eth2.

---

### Post by houserparker on 2009-11-05
> **kixome said:**
> IN /ETC/NETWORK/INTERFACES change eth0 to eth2

I have done this but then i can no longer see any networks.

---

### Post by kixome on 2009-11-05
try posting ifconfig -a

---

### Post by kixome on 2009-11-05
> **houserparker said:**
> I have done this but then i can no longer see any networks.

does it work with eth0? if so leave it alone. also previous guys post being relevant, is this a wired/wireless connection?

---

### Post by houserparker on 2009-11-05
> **kixome said:**
> does it work with eth0? if so leave it alone. also previous guys post being relevant, is this a wired/wireless connection?

Im using the internet now with it configured to eth0 but as yo0u requested it doesnt appear that there is any activity on eth0. I can leave it configured as eth0 but  is there any way of knowing whether i have a static ip or whether its working? 

ben@ben-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:cc:37:6d:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:24:2c:15:5b:bc  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe15:5bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11837 errors:0 dropped:0 overruns:0 frame:8676
          TX packets:9357 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12980624 (12.9 MB)  TX bytes:1261417 (1.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9238 (9.2 KB)  TX bytes:9238 (9.2 KB)

---

### Post by kixome on 2009-11-05
yes, are you able to browse the internet with this connection? if so it is working. Not being a smart butt just reiterating that it is working. from terminal:
ping yahoo.com

if you get a reply it is working.

---

### Post by kixome on 2009-11-05
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:[COLOR="Red"]11837[/COLOR] errors:0 dropped:0 overruns:0 frame:[COLOR="Red"]8676[/COLOR]
TX packets[COLOR="Red"]:9357[/COLOR] errors:6 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
[COLOR="Red"]RX bytes:12980624 (12.9 MB) TX bytes:1261417 (1.2 MB)[/COLOR]
Interrupt:18

should be working

---

### Post by kixome on 2009-11-05
also I think in ubuntu that your default working connection is eth0 in interfaces even if it truly is not, i think the ubu scripts/programming make this so. even if ifconfig lists as eth2

---

### Post by houserparker on 2009-11-05
I pinged yahoo and this is what it returned.

ben@ben-laptop:~$ ping yahoo.com
PING yahoo.com (209.191.93.53) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Port Unreachable
From 192.168.0.2 icmp_seq=2 Destination Port Unreachable
From 192.168.0.2 icmp_seq=3 Destination Port Unreachable
From 192.168.0.2 icmp_seq=4 Destination Port Unreachable
From 192.168.0.2 icmp_seq=5 Destination Port Unreachable
From 192.168.0.2 icmp_seq=6 Destination Port Unreachable
From 192.168.0.2 icmp_seq=7 Destination Port Unreachable
From 192.168.0.2 icmp_seq=8 Destination Port Unreachable
From 192.168.0.2 icmp_seq=9 Destination Port Unreachable
From 192.168.0.2 icmp_seq=10 Destination Port Unreachable
From 192.168.0.2 icmp_seq=11 Destination Port Unreachable

From 192.168.0.2 icmp_seq=12 Destination Port Unreachable
From 192.168.0.2 icmp_seq=13 Destination Port Unreachable

---

### Post by panicy on 2009-11-05
what about when you ping the gateway?  If your getting an ip of .0.2 it seems the communiation to the router is ok, but I would still ping .0.1 to make sure.  Also, try pinging an ip rather then a domain name to check and see if its a dns issue.  Ping 4.2.2.2 (main dns server of ALL dns servers... thus alway up).  What do you get?

---

### Post by iruel on 2009-11-05
try this command
```

ifconfig eth0 192.168.0.2/24 up
route add default gw 192.168.0.1

```
and you can set DNS if it's still can't connected on **/etc/resolv.conf** by added this line
**namespace 192.168.0.1**

;)

---

### Post by houserparker on 2009-11-05
> **panicy said:**
> what about when you ping the gateway?  If your getting an ip of .0.2 it seems the communiation to the router is ok, but I would still ping .0.1 to make sure.  Also, try pinging an ip rather then a domain name to check and see if its a dns issue.  Ping 4.2.2.2 (main dns server of ALL dns servers... thus alway up).  What do you get?

This what this returned. Any ideas on what this means. If this makes a difference i am using moblock primary threat blocklist which im sure isnt anywhere near these ip's. 

PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Port Unreachable
From 192.168.0.3 icmp_seq=2 Destination Port Unreachable
From 192.168.0.3 icmp_seq=3 Destination Port Unreachable
From 192.168.0.3 icmp_seq=4 Destination Port Unreachable
From 192.168.0.3 icmp_seq=5 Destination Port Unreachable
From 192.168.0.3 icmp_seq=6 Destination Port Unreachable
From 192.168.0.3 icmp_seq=7 Destination Port Unreachable
From 192.168.0.3 icmp_seq=8 Destination Port Unreachable
From 192.168.0.3 icmp_seq=9 Destination Port Unreachable
From 192.168.0.3 icmp_seq=10 Destination Port Unreachable
From 192.168.0.3 icmp_seq=11 Destination Port Unreachable
From 192.168.0.3 icmp_seq=12 Destination Port Unreachable
From 192.168.0.3 icmp_seq=13 Destination Port Unreachable

---

### Post by houserparker on 2009-11-05
> **iruel said:**
> try this command
```

ifconfig eth0 192.168.0.2/24 up
route add default gw 192.168.0.1

```and you can set DNS if it's still can't connected on **/etc/resolv.conf** by added this line
**namespace 192.168.0.1**

;)

This what the code returned

ben@ben-laptop:~$ ifconfig eth0 192.168.0.2/24 up
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
ben@ben-laptop:~$ route add default gw 192.168.0.1
SIOCADDRT: Operation not permitted
ben@ben-laptop:~$

Any ideas on what this means?

---

### Post by kixome on 2009-11-05
use sudo before the commands
and enter pass

---

### Post by kixome on 2009-11-05
most here expect that ppl know to:

sudo "command without quotes" whatever blah

---

### Post by houserparker on 2009-11-05
Im not sure whether its supposed to do this but the adress hilighted below has changed.

ben@ben-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:cc:37:6d:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:24:2c:15:5b:bc  
         **[COLOR=Red] inet addr:192.168.0.3[/COLOR]**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe15:5bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58187 errors:0 dropped:0 overruns:0 frame:21167
          TX packets:79760 errors:122 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29779968 (29.7 MB)  TX bytes:65104466 (65.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74310 (74.3 KB)  TX bytes:74310 (74.3 KB)

---

### Post by iruel on 2009-11-05
try to deactive eth2 first with this command
```

sudo ifconfig eth2 down

```
and then try to set eth0 again,follow my post before

---

