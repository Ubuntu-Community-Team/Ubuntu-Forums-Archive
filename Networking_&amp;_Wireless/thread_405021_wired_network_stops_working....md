---
title: "wired network stops working..."
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by paca on 2007-04-09
Hi !
I'v a problem with my ubuntu installation, using edgy eft server, and newest kernel (2.6.20.6).
Network just stops working, everything looks good.. but doesnt work. when i do network restart it works again...
I'v tried different NIC's (broadcom, dlink) gbit... same outcome...
works from a few min to a couple of hours tops..

any ideas would be welcome! im all out :(

please help!

---

### Post by dbott67 on 2007-04-09
Are you using static IP or DHCP?

When you say "stops working" what do you mean:
- no connectivity at all (can't ping any device; local or internet)
- can ping but can't surf (i.e. no DNS resolution)
- are there other devices on the same network that work fine when this is happening

When the server is _**working**_, can you post the output of the following commands:
```
dbott@feisty:~$ [COLOR=Red]**ifconfig -a**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:**[COLOR=Red]192.168.1.106[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114990474 (109.6 MiB)  TX bytes:19497853 (18.5 MiB)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89440 (87.3 KiB)  TX bytes:89440 (87.3 KiB)

``````
dbott@feisty:~$ [COLOR=Red]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         [COLOR=Red]**192.168.1.1**[/COLOR]     0.0.0.0         UG    0      0        0 eth0
```
```
dbott@feisty:~$ [COLOR=Red]**cat /etc/resolv.conf **[/COLOR]
nameserver 192.168.1.1

```Also, ping the following devices:
```
dbott@feisty:~$[COLOR=Red]** ping localhost -c4**[/COLOR]
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.049 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.049 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.051 ms

--- localhost ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.049/0.050/0.051/0.001 ms

dbott@feisty:~$ [COLOR=Red]**ping 192.168.1.106 -c4  ***[COLOR=Blue]# IP address of your machine[/COLOR]*[/COLOR]
PING 192.168.1.106 (192.168.1.106) 56(84) bytes of data.
64 bytes from 192.168.1.106: icmp_seq=1 ttl=64 time=0.061 ms
64 bytes from 192.168.1.106: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 192.168.1.106: icmp_seq=3 ttl=64 time=0.049 ms
64 bytes from 192.168.1.106: icmp_seq=4 ttl=64 time=0.053 ms

--- 192.168.1.106 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.049/0.053/0.061/0.007 ms

dbott@feisty:~$ [COLOR=Red]**ping 192.168.1.1 -c4 **[/COLOR]*[COLOR=Red][COLOR=Blue]# IP address of your gateway (from route -n)[/COLOR][/COLOR]*
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=0.594 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=0.579 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=0.579 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=127 time=0.593 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.579/0.586/0.594/0.018 ms

dbott@feisty:~$ [COLOR=Red]**ping www.google.com -c4  **[/COLOR]*[COLOR=Red][COLOR=Blue]# some known-working FQDN[/COLOR][/COLOR]*
PING www.l.google.com (64.233.161.99) 56(84) bytes of data.
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=1 ttl=234 time=44.3 ms
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=2 ttl=234 time=42.7 ms
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=3 ttl=234 time=43.7 ms
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=4 ttl=234 time=46.9 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 42.786/44.462/46.953/1.562 ms

dbott@feisty:~$ **[COLOR=Red]ping 64.233.161.99 -c4[/COLOR]** * [COLOR=Blue]# IP address of www.google.com from above[/COLOR]*
PING 64.233.161.99 (64.233.161.99) 56(84) bytes of data.
64 bytes from 64.233.161.99: icmp_seq=1 ttl=234 time=42.2 ms
64 bytes from 64.233.161.99: icmp_seq=2 ttl=234 time=43.7 ms
64 bytes from 64.233.161.99: icmp_seq=3 ttl=234 time=43.0 ms
64 bytes from 64.233.161.99: icmp_seq=4 ttl=234 time=43.9 ms

--- 64.233.161.99 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 42.256/43.222/43.904/0.697 ms

```Then, when the **_server stops working_**, try doing the above commands again and post the results.  This will help us determine when the problem lies (computer, DHCP, DNS, router, etc.)

-Dave

---

### Post by paca on 2007-04-09
static IP,
and cant ping anything local or internet.. just localhost.
all other devices on the same network are working...
i'll post the commands later today (cant connect to the box) heh
forgot, using ip not hostnames so cant be dns...

---

### Post by dbott67 on 2007-04-09
Okay, thanks.

When you get a chance, post the output of your routing table (route -n) and your interfaces file (cat /etc/network/interfaces) while it's working and then again when it stops.

Also, can you describe the network topology (home network with D-Link router; university campus; work, etc.), your ISP (cable, DSL, etc.).  I just need to get a visual of what's going on.

-Dave

---

### Post by grkravi on 2007-04-15
I too have this problem... i am having edgy on my dell laptop, upgraded my kernel first to 2.6.20.6 and then to 2.6.20.7 and i couldn't surf. DHCP is working fine and i am able to ping my gateway, localhost and my ip address.
I am using firestarter and it keeps blocking me from surfing...but if i allow the connectivity from firestarter, i am able to connect. With connectivity enabled for google, i am able to ping google, but not other web sites.
Is there a simple way to open the firewall for internet access ? i didnt had to do this in kernel  2.6.17 internet connectivity was enabled by default.

---

