---
title: "VPN Connection Not Working"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by groberts1980 on 2006-08-14
For a new job I have just taken, I have to connect to a VPN before I can access their internal web server. It is a PPTP connection. Server type is PPP. I was able to get the VPN up and running and was able to connect in XP, but now I'm trying to get it up and running with Ubuntu.

I installed pptp-linux and I'm running pptpconfig tunnel right now. I put in the server and username/password and it looks like it connected just fine. In the application window it says "pptpconfig: connected"

Problem is, I can't connect to the company's internal web server. Can anybody  tell me what the problem is, or even if I'm running the right program for this?

I've only been running Ubuntu since last weekend, so I'm very new to Linux. Any help would be greatly appreciated.

Edit: After playing with the options for pptconfig, I was able to connect to the VPN. I guess I posted my problem a little too early. But, if anyone wants to recommend any other VPN connection utilities, I'd take any suggestions.

---

### Post by 1oki on 2006-08-29
what type of tunnel are you running? Lan to Lan, all tunnel? there is another thread where we are talking about pptpconfig if you want to go there...

[http://www.ubuntuforums.org/showthread.php?t=236710](http://www.ubuntuforums.org/showthread.php?t=236710)

some of the original people who posted might know... or I can try...

---

### Post by Geoff2077 on 2006-08-30
Out of interest - after you establish the VPN connection - how do you access the files or folders on your remote server??

---

### Post by 1oki on 2006-08-31
who are you talking to geoff? me or him?

---

### Post by steve.horsley on 2006-08-31
It sounds to me as though maybe the routing isn't being set up. After creating the tunnel, you have to create a route saying that the company network is accessible via **this** (ppp0?) interface. 

Can you set the tunnel up and then try these commands to see what's going on?
[B]ifconfig
route -nw
ifconfig
route -n[/B]

---

### Post by Geoff2077 on 2006-08-31
HiSteve,
Here the result..
root@linux:/home/geoff# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.16.50  P-t-P:192.168.16.157  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:98 (98.0 b)  TX bytes:104 (104.0 b)

ra0       Link encap:Ethernet  HWaddr 00:16:B6:98:48:B1
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe98:48b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:1641528 (1.5 MiB)  TX bytes:41243 (40.2 KiB)
          Interrupt:169

root@linux:/home/geoff# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.16.157  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
61.9.197.80     192.168.1.1     255.255.255.255 UGH   0      0        0 ra0
192.168.16.2    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
192.168.16.0    0.0.0.0         255.255.255.0   U     0      0        0 ppp0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
root@linux:/home/geoff# route -v
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.16.157  *               255.255.255.255 UH    0      0        0 ppp0
cpe-61-9-197-80 192.168.1.1     255.255.255.255 UGH   0      0        0 ra0
gptaserv01.gpta *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0
192.168.16.0    *               255.255.255.0   U     0      0        0 ppp0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
root@linux:/home/geoff#

the ip address of our server is 192.168.16.2. It is also named gptaserv01

Cheers
Geoff

---

### Post by steve.horsley on 2006-09-02
Well, you have a route to the correct network then. I, fact, you have two routes that should do the trick - a network route to 192.168.16.0 and a host route to 192.168.16.2, both pointing over ppp0. I don't see why you can't access the server, at least by IP address. 

Can you ping it? **ping 192.168.16.2**
Can you ping it by name? **ping gptaserv01**
Can you browse it by IP address? **[http://192.168.16.2/](http://192.168.16.2/)**

If you can access it by IP address but not by name, the problem is with name resolution.  You may have to add a different DNS server to /etc/resolv.conf while the PPP VPN is up. That's a bit tricky, and it may be easier to edit /etc/hosts and make a permanent local entry in there.

---

### Post by Geoff2077 on 2006-09-04
Hi Steve,
I can ping the ip address 192.168.16.2 but not the name gptaserv01 (host unknown).

[http://gptaserv01/](http://gptaserv01/) or [http://192.168.16.2/](http://192.168.16.2/) do not respond, as we dont have a web server running on the win 2000 SBS.

I dont understand what I need to do to view the folders on this server, given that I have apparently establishe the vpn connection, using pptpconfig.


Appreciate any further assistance you might suggest...

Geoff

---

