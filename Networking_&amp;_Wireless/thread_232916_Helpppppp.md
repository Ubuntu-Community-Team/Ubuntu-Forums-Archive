---
title: "Helpppppp"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by moataz on 2006-08-09
hey all,

after downloading certain updates this has happened:
1) i cant ping to anything at all and i keep getting "ping: sendmsg: operation not permitted"
or i get 
2) destination host unreachable and i can only get through to my router....

heres a detailed dump of the problem....

moataz@ubuntu:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.51 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.14 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.14 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.14 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=2.15 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=2.16 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=2.12 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=2.16 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9035ms
rtt min/avg/max/mdev = 2.126/2.189/2.513/0.123 ms
moataz@ubuntu:~$ ping -c 10 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.161.104) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9000ms

moataz@ubuntu:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 163.121.138.134
nameserver 212.103.160.18
moataz@ubuntu:~$ iptables -L INPUT
iptables v1.3.3: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
moataz@ubuntu:~$ sudo iptables -L INPUT
Password:
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  dns-cache.tedata.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  dns-cache.tedata.net  anywhere
ACCEPT     tcp  --  ns1.tedata.net       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  ns1.tedata.net       anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.1.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'
moataz@ubuntu:~$ sudo iptables -L OUTPUT
Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.3          dns-cache.tedata.net tcp dpt:domain
ACCEPT     udp  --  192.168.1.3          dns-cache.tedata.net udp dpt:domain
ACCEPT     tcp  --  192.168.1.3          ns1.tedata.net      tcp dpt:domain
ACCEPT     udp  --  192.168.1.3          ns1.tedata.net      udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
moataz@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:76:67:8D
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe76:678d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1777 errors:143 dropped:0 overruns:0 frame:143
          TX packets:1364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:348925 (340.7 KiB)  TX bytes:135085 (131.9 KiB)
          Interrupt:193 Memory:f8b80000-f8b90000

eth0      Link encap:Ethernet  HWaddr 00:02:3F:83:95:8A
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31788 (31.0 KiB)  TX bytes:1692 (1.6 KiB)
          Interrupt:185 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2972 (2.9 KiB)  TX bytes:2972 (2.9 KiB)


if anyone knows what i should do please advice me. thanks:)

---

### Post by Paerez on 2006-08-09
well if you are connected to your router/gateway fine (192.168.1.1), but not to google, my guess is that your router has problems. Try turning it off and on again.

---

### Post by tagra123 on 2006-08-09
Try this:

MENU: System - Administration - Networking

Make sure the default gateway device is correct (eth0) should be since you can connect to your router.

Next:

Click on Ethernet and then on Properties  if static the line should read something like this

IP Address   192.168.1.50
Subnet Mask  255.255.255.0
Gateway      192.168.1.1

click on Ok

Next click on the  DNS tab

enter your DNS Servers (ISP PROVIDERS DNS) here by clicking the add button.

You can usually find the dns these in you routers settings.

Some routers will allow this to work by simply entering  192.168.1.1 as the dns server but I usually enter the actual IPs


Click on OK.

Try starting your web browser again.

Hope it helps you.



You may also consider installing firestarter - ip something if iptable is blocking something you can turn off the firewall completely and see iif the connection starts working. Then turn it back on and find out which ports are being blocked and causing problems.

---

### Post by moataz on 2006-08-09
i did all of that, still nothing changed, on firestarter the received packets increase and the sent packets are "0"

any other ideas ?

---

### Post by tagra123 on 2006-08-09
I looked at your previous post.

The ping times on your router look like they are taking too long.

I thing the times should be closer to 0.123 MS

Is this a Eithernet or Wireless router ?

What brand?

From looking at your ifconfig output I see you have a wireless and wired network?

Instead of using eth0 -- try using ath0 as the default.

Also do you have wireless wep security - turn it off until you get everything working or make sure you have the wep number correct.

If you are using the wireless card try disabling the ethernet card either by removing it or disabling it in the bios if it is built in. 

Try doing a factory reset and see if it helps.

---

