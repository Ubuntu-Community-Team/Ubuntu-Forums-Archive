---
title: "Can't access Internet - Netgear DG632"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by thema832 on 2006-08-19
Hello,
I can’t use Internet from my new Ubuntu 6.06 system. All my trials from firefox end with:
 « The connection has timed out The server at [www.dilbert.com](www.dilbert.com) is taking too long to respond. » 

Firefox is configured without proxy (Firefox preferences: direct connection to the internet). The issue doesn’t seem to be with firefox anyway, because Synaptic brings the same kind of error (Could not download all repository indexes).

Config details : Shuttle ST20G5 with integrated network controller  Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11) –see :~$ sudo lspci –v below.-

Modem router ADSL Netgear DG632
The same modem, connected via the Ethernet port on a windows system works perfectly, which I  think excludes problem related to PPPOA, MTU and the like. 
The firewall of the modem is not activated.
The modem is used as DHCP server (except when configured with fixed IP address below) and DNS server.
I do not think that it is a DNS issue, because dig works:
dig [www.pagesjaunes.fr](www.pagesjaunes.fr)
; <<>> DiG 9.3.2 <<>> [www.pagesjaunes.fr](www.pagesjaunes.fr)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31022
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.pagesjaunes.fr](www.pagesjaunes.fr).            IN      A

;; ANSWER SECTION:
[www.pagesjaunes.fr](www.pagesjaunes.fr).     3032    IN      A       193.252.242.142
[www.pagesjaunes.fr](www.pagesjaunes.fr).     3032    IN      A       193.252.242.225

;; Query time: 55 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Aug  1 21:30:26 2006
;; MSG SIZE  rcvd: 68

Ping works too:
~$ ping -c60 [www.orange.fr](www.orange.fr)
PING [www.orange.fr](www.orange.fr) (193.252.122.103) 56(84) bytes of data.
64 bytes from [www.orange.fr](www.orange.fr) (193.252.122.103): icmp_seq=1 ttl=245 time=50.3 ms
64 bytes from [www.orange.fr](www.orange.fr) (193.252.122.103): icmp_seq=2 ttl=245 time=50.8 ms
64 bytes from [www.orange.fr](www.orange.fr) (193.252.122.103): icmp_seq=3 ttl=245 time=50.5 ms


--- [www.orange.fr](www.orange.fr) ping statistics ---
60 packets transmitted, 60 received, 0% packet loss, time 59339ms
rtt min/avg/max/mdev = 48.202/55.200/229.879/23.628 ms

Below the result of ifconfig…
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:B9:0A:E3
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb9:ae3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:61138 (59.7 KiB)  TX bytes:61344 (59.9 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:908 (908.0 b)  TX bytes:908 (908.0 b)

…of route…
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway.ar7   0.0.0.0         UG    0      0        0 eth0

and of lspci –v for the network controller:
:~$ sudo lspci -v
Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device f391
        Flags: bus master, fast devsel, latency 0, IRQ 209
        Memory at dfef0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
        Capabilities: [d0] #10 [0001]

Everything looks good to me…
…I tried anyway to configure eth0 with a fixed IP address:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:B9:0A:E3
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb9:ae3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:97680 (95.3 KiB)  TX bytes:51549 (50.3 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:708 (708.0 b)  TX bytes:708 (708.0 b)

And on the router console:
Address Reservation
 	# 	IP Address	Device Name	MAC Address
	1	192.168.0.2	eth0	00:30:1B:B9:0A:E3

This doesn’t change dig or ping (they still work correctly) but doesn’t help for browsing:
--- 216.219.72.36 ping statistics ---
60 packets transmitted, 60 received, 0% packet loss, time 59392ms
rtt min/avg/max/mdev = 57.058/58.572/61.439/1.024 ms

 <<>> DiG 9.3.2 <<>> [www.hotmail.com](www.hotmail.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20232
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.hotmail.com](www.hotmail.com).               IN      A

;; ANSWER SECTION:
[www.hotmail.com](www.hotmail.com).        2073    IN      CNAME   [www.hotmail.com.nsatc.net](www.hotmail.com.nsatc.net).
[www.hotmail.com.nsatc.net](www.hotmail.com.nsatc.net). 1446 IN      CNAME   [www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net).
[www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net). 261 IN      A       216.219.72.36
[www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net). 261 IN      A       166.63.208.158
[www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net). 261 IN      A       208.173.208.152

;; Query time: 55 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Fri Aug 18 18:56:22 2006
;; MSG SIZE  rcvd: 151

I then tried to add in Ubuntu as DNS server the DNS of my provider: no improvement.
On the advice of a friend, and to try to solve a potential negotiation issue between the shuttle and the netgear ethernet interface, I eventually tried: 
~$ sudo mii-tool -F 100baseTX-FD eth0 
No improvement.
I am no network expert and this is beyond me. Anybody sees what has escaped me? What may I try to improve the diagnostic?
Thanks!

---

### Post by TripleE on 2006-08-19
Both firefox and synaptic use port 80 (http) to request traffic.  Your IP address, internet connectivity and DNS all look to be working/good.  Somewhere something (router or a local firewall) is blocking port 80 from being sent out.  I would recommend plugging your computer directly to your cable/dsl modem and see if it works.  If it does not, I would say a local firewall is blocking the traffic.

---

### Post by thema832 on 2006-08-19
My modem/router is connected directly to my PC. The firewall function of the routeur is not activated. Is there a possibility that a software firewall is implemented as standard with Ubuntu 6.06 and blocks traffic on 80 (I realize the question is silly, but I fail to see another explanation along the FW line)?
Is there a way in command mode to check if the port 80 is open ?
Thanks for your sugestion.

---

### Post by thema832 on 2006-08-21
Still trying to understand what's wrong with my access: below the result of wget
:~$ wget 216.219.72.36
--22:35:24--  [http://216.219.72.36/](http://216.219.72.36/)
           => `index.html'
Connecting to 216.219.72.36:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://login.live.com/login.srf?id=2&svc=mail&cbid=24325&msppjph=1&tw=0&fs=1&fsa=1&fsat=1296000&lc=1033&_lang=EN](http://login.live.com/login.srf?id=2&svc=mail&cbid=24325&msppjph=1&tw=0&fs=1&fsa=1&fsat=1296000&lc=1033&_lang=EN) [following]
--22:35:24--  [http://login.live.com/login.srf?id=2&svc=mail&cbid=24325&msppjph=1&tw=0&fs=1&fsa=1&fsat=1296000&lc=1033&_lang=EN](http://login.live.com/login.srf?id=2&svc=mail&cbid=24325&msppjph=1&tw=0&fs=1&fsa=1&fsat=1296000&lc=1033&_lang=EN)
           => `login.srf?id=2&svc=mail&cbid=24325&msppjph=1&tw=0&fs=1&fsa=1&fsat=1296000&lc=1033&_lang=EN'
Resolving login.live.com... 1.0.0.0
Connecting to login.live.com|1.0.0.0|:80... failed: Network is unreachable.
The way I read this, the first HTTP request went through, so port 80 must be open? And then, network is unreachable. Am I wrong reading this ? All new ideas welcome!

---

### Post by thema832 on 2006-08-21
The issue is solved. From reading various forums, looks like it was the proxy DNS feature of the netgear that behaved strangely when "talking" with the IPv6 stack present by default in Ubuntu. Quick fix: I configured eth0 as a fixed IP address so that resolv.conf is not overwrite at boot, and then removed the netgear address as DNS server, replacing it with the DNS of my ISP. No elegant, but efficient. Other posts suggested removing the IPv6 stack from Ubuntu. Haven't tested it though...

---

