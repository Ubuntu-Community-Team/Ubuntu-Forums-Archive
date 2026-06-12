---
title: "Internet - Broadband"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Aravind Kumar on 2007-03-21
I am currently using Ubuntu 6.06 and have problems connecting to the Internet. I have Enabled the Ethernet card, and have set other details in the Network settings. But I am not able browse through Firefox or get any updates. But when I was using Ubuntu 5.10 it was working fine. Any help???

---

### Post by lloyd_b on 2007-03-21
Could you post some additional information?

1.  The output from running the "ifconfig" command in a terminal window.
2.  The output from running the "route -n" command in a terminal window.
3.  The contents of the file "/etc/network/interfaces"
4.  The contents of the file "/etc/resolv.conf"

Sorry to ask for all that, but with the limited information provided in the initial post there are simply too many possibilities.  The info I've requested should narrow down the issue.

Lloyd B.

---

### Post by Aravind Kumar on 2007-03-22
output of ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:40:F4:ED:D3:7A
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:feed:d37a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12455 (12.1 KiB)  TX bytes:7136 (6.9 KiB)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)
________________________________________________________________________________________

output of route -n :

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0              UG    0      0        0 eth0
________________________________________________________________________________________

contents of /etc/network/interfaces :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
________________________________________________________________________________________

contents of /etc/reslov.conf :

nameserver 61.1.96.69
nameserver 61.1.96.71
________________________________________________________________________________________

---

### Post by chewearn on 2007-03-22
Looks ok, as far as I can tell.

You have your gateway ip at 192.168.1.1.  Is that your internet modem/router ?
Can you ping that address ?
Can you ping [www.google.com](www.google.com) ?

---

### Post by Aravind Kumar on 2007-03-22
I have also attached the data due to the formatting problems with the posting.

---

### Post by Aravind Kumar on 2007-03-22
192.168.1.1 is my DSL modem.
I can ping that address but not any other!!!

---

### Post by chewearn on 2007-03-22
Your output are very close to mine; I don't think there is anything wrong with the ubuntu network setup.  Furthermore, you can ping your DSL modem, and I don't see errors or dropped packets.  The connections from your ubuntu PC to the modem appeared to be working.

Could you verify that the DSL modem is actually properly connected?  Or have the correct setup?  Do you require proxy settings (is it properly configured)?

If you have another machine to connect to the DSL modem, you can also check if the machine can access the internet.

---

### Post by lloyd_b on 2007-03-22
Okay, I only see two possibilities remaining:
1.  The router can't get to the internet.
2.  There's a problem with DNS (the nameservers).

In a terminal, please try the following:
```
ping 66.102.7.99
```
(That's an IP for "www.google.com"). 

If that doesn't work, then most likely the problem is the link between your DSL modem and your ISP.  Just to confirm:
```
traceroute 66.102.7.99
```
and you should see your DSL modem/router, but nothing beyond it.  If this turns out to be the case, you need to contact your ISP's tech support to resolve the issue.

If that ping does work, then the problem is probably with name resolution.  Try this:
```
ping 61.1.96.69
ping 61.1.96.71
```
Those are the two nameservers you have defined (in resolv.conf).  If neither of those respond, then you've identified the problem.  Again - you'll need to contact your ISP's tech support, to identify the correct nameservers.

Please run the above tests, and let us know what the results were. 

Lloyd B.

---

### Post by Aravind Kumar on 2007-03-23
Results of ping 66.102.7.99

PING 66.102.7.99 (66.102.7.99) 56(84) bytes of data.
64 bytes from 66.102.7.99: icmp_seq=1 ttl=239 time=287 ms
64 bytes from 66.102.7.99: icmp_seq=2 ttl=239 time=305 ms
64 bytes from 66.102.7.99: icmp_seq=3 ttl=239 time=303 ms
64 bytes from 66.102.7.99: icmp_seq=4 ttl=239 time=291 ms
64 bytes from 66.102.7.99: icmp_seq=5 ttl=239 time=302 ms

--- 66.102.7.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 287.721/298.103/305.454/7.122 ms
___________________________________________________________________________________

And when I issued the traceroute command it said command not found...

___________________________________________________________________________________

Result of ping 61.1.96.69

PING 61.1.96.69 (61.1.96.69) 56(84) bytes of data.

--- 61.1.96.69 ping statistics ---
82 packets transmitted, 0 received, 100% packet loss, time 81130ms
___________________________________________________________________________________

Result of ping 61.1.96.71

PING 61.1.96.71 (61.1.96.71) 56(84) bytes of data.

--- 61.1.96.71 ping statistics ---
58 packets transmitted, 0 received, 100% packet loss, time 57043ms
___________________________________________________________________________________


Actually when I issued the last two ping commands nothin turned up and so I had to 
eventually cut the pinging myself using ctrl + C...

I also have windows XP in which these DNS ips work fine. I am able to connect to
internet easily in windows. With the IP u gave for google I was able to connect to
google's page easily. So I googled for ubuntuforums.org ip and found one. I'm happy 
to make this post using Linux and Firefox which I love very much. Any help!!!

---

### Post by lloyd_b on 2007-03-23
> Results of ping 66.102.7.99

PING 66.102.7.99 (66.102.7.99) 56(84) bytes of data.
64 bytes from 66.102.7.99: icmp_seq=1 ttl=239 time=287 ms
64 bytes from 66.102.7.99: icmp_seq=2 ttl=239 time=305 ms
64 bytes from 66.102.7.99: icmp_seq=3 ttl=239 time=303 ms
64 bytes from 66.102.7.99: icmp_seq=4 ttl=239 time=291 ms
64 bytes from 66.102.7.99: icmp_seq=5 ttl=239 time=302 ms

--- 66.102.7.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 287.721/298.103/305.454/7.122 ms
__________________________________________________ _________________________________

And when I issued the traceroute command it said command not found...

So the network connection itself is fine.  To get traceroute, you need to install the package ("traceroute"), which may be a bit difficult since you don't have reliable access to the repositories.  Ouch.

> Result of ping 61.1.96.69

PING 61.1.96.69 (61.1.96.69) 56(84) bytes of data.

--- 61.1.96.69 ping statistics ---
82 packets transmitted, 0 received, 100% packet loss, time 81130ms
__________________________________________________ _________________________________

Result of ping 61.1.96.71

PING 61.1.96.71 (61.1.96.71) 56(84) bytes of data.

--- 61.1.96.71 ping statistics ---
58 packets transmitted, 0 received, 100% packet loss, time 57043ms
__________________________________________________ _________________________________


Actually when I issued the last two ping commands nothin turned up and so I had to
eventually cut the pinging myself using ctrl + C...
This is exactly what you would expect to see if the nameservers are not accessible.  

> I also have windows XP in which these DNS ips work fine. I am able to connect to
internet easily in windows. With the IP u gave for google I was able to connect to
google's page easily. So I googled for ubuntuforums.org ip and found one. I'm happy
to make this post using Linux and Firefox which I love very much. Any help!!!
I'm afraid that I don't know what to try next.  The issue is DNS - your Ubuntu box cannot reach those nameservers, and as a result any attempt to access a host by name is failing. 

Could you double-check those IP addresses in XP?  Be careful to watch for simple typographical errors, such as transposed digits.

Lloyd B.

---

### Post by Aravind Kumar on 2007-03-24
The ISP's tech support said that if the nameservers weren't doin the job, they asked me try 192.168.1.1 which works partially. I am now able to browse without typing the IP's which I had to do yesterday. The small prob is that the connection is not continuous for a long time. But by typing the IP myself the page gets loaded instantly.
I express my gratitude to those who helped in this issue. And a special thanks to Mr. lloyd_b. I am happy to use Internet through Ubuntu...

---

