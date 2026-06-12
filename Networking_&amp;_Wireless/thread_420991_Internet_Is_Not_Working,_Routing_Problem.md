---
title: "Internet Is Not Working, Routing Problem?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by smurakozi on 2007-04-24
Hi,

Yesterday I've tried the ubuntu 7.04 live CD on my PC (with an ABIT NF-M2 motherboard). Most things work fine, but I have problems with networking using a cable modem with DHCP.
I've checked the networking settings based on some network troubleshooting guides, and everything has reasonable values (network card is identified correctly, I have a valid IP address and MAC address and two DNS servers). I also checked several log files (e.g. boot.messages), but found no errors.
If I try to ping a host (which is not in my ISP's LAN), then the ip address is resolved, but after that nothing happens, no errors, just no reply.
It's a bit strange for me that I can ping one of my DNS servers, but not the other (therefore I also tried to use only the one I could ping, no success).
When I tried tracepath, it showed that it can get only to my ISP but not further.

I had exactly the same experience with openSUSE 10.2: everything works fine, except for the network.

I also have a laptop with openSUSE 10.1 (which was updated from 10.0), and it can use the same modem with the same cable without problems, so I guess the modem and cables are ok.

Do you have any idea what settings/log files/tools should I also check?

Thanks in advance,
don

---

### Post by lloyd_b on 2007-04-24
A routing problem is a definite possibility.  Could you post some additional info, to help us diagnose the problem?

(Note: all commands should be run from a terminal window)
1.  The output from running "ifconfig"
2.  The output from from running "route -n" 
3.  The output from running "nslookup www.google.com"
4.  The output from running "traceroute www.google.com" (note: if it responds with "command not found", try installing the "traceroute" package).

Lloyd B.

---

### Post by smurakozi on 2007-04-24
Hi Lloyd,
thanks for the quick reply.

Here are the outputs of those commands:

1. The output from running "ifconfig"

eth0      Link encap:Ethernet  HWaddr 00:50:8D:95:0F:28  
          inet addr:10.106.89.230  Bcast:10.106.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:8dff:fe95:f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:260606 (254.4 Kb)  TX bytes:2457 (2.3 Kb)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3254 (3.1 Kb)  TX bytes:3254 (3.1 Kb)
 

2. The output from from running "route -n"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.106.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         10.106.0.1      0.0.0.0         UG    0      0        0 eth0 

3. The output from running "nslookup www.google.com"

Server:		193.110.57.4
Address:	193.110.57.4#53

Non-authoritative answer:
[www.google.com](www.google.com)	canonical name = [www.l.google.com](www.l.google.com).
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.99
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.103
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.104
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.147
 
4. The output from running "traceroute www.google.com".

traceroute to [www.google.com](www.google.com) (64.233.183.103), 30 hops max, 40 byte packets
 1  core.hdsnet.hu (86.127.41.1)  7.691 ms   9.269 ms   11.092 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * * 


Will it be enough to find the problem, or you need more info?

Thanks again,
don

---

### Post by lloyd_b on 2007-04-24
Okay, that is a bit weird.

1. "ifconfig" looks normal.  You're getting a valid IP, with a believable netmask.
2.  "route" looks okay.  Your gateway is (10.106.0.1) is properly defined.
3.  "nslookup" is getting good info for Google.
4.  This I do not understand:

Since your gateway is at 10.106.0.1, I would expect that to be the first response in any traceroute path.  But you're getting a completely different first response (86.127.41.1).  Possibly this is the problem, or it might just be an artifact of the way your cable modem/ISP operates.

So we can now confirm exactly what you told us in the original message:) 

Since I don't see anything significant, time for a comparison:  Could you connect that Suse box, and run the same commands on it?  

Lloyd B.

---

### Post by smurakozi on 2007-04-25
Hi,

I got these when executed the commands on my laptop:

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:90:F5:28:B0:F8  
          inet addr:82.77.96.231  Bcast:82.77.96.255  Mask:255.255.255.128
          inet6 addr: fe80::290:f5ff:fe28:b0f8/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1697449 (1.6 Mb)  TX bytes:255129 (249.1 Kb)
          Interrupt:217 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3260 (3.1 Kb)  TX bytes:3260 (3.1 Kb)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
82.77.96.128    0.0.0.0         255.255.255.128 U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         82.77.96.129    0.0.0.0         UG    0      0        0 eth0

nslookup:

Server:		193.110.57.4
Address:	193.110.57.4#53

Non-authoritative answer:
[www.google.com](www.google.com)	canonical name = [www.l.google.com](www.l.google.com).
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.147
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.99
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.103
Name:	[www.l.google.com](www.l.google.com)
Address: 64.233.183.104


traceroute:

traceroute to [www.google.com](www.google.com) (64.233.183.104), 30 hops max, 40 byte packets
 1  core.hdsnet.hu (86.127.41.1)  7.921 ms   7.454 ms   8.494 ms
 2  xr01.budapest.rdsnet.ro (213.154.125.25)  8.330 ms   20.221 ms   9.272 ms
 3  br01.frankfurt.rdsnet.ro (193.231.252.45)  34.512 ms   32.693 ms   39.307 ms
 4  xr01.frankfurt.rdsnet.ro (213.154.124.14)  33.319 ms   33.808 ms   33.469 ms
 5  de-cix10.net.google.com (80.81.192.108)  31.959 ms   41.269 ms   37.981 ms
 6  209.85.249.178  36.858 ms   34.718 ms   33.722 ms
 7  72.14.232.208  40.972 ms   42.237 ms   47.216 ms
 8  72.14.232.141  46.862 ms 209.85.248.182  30.708 ms   30.890 ms
 9  72.14.233.77  34.382 ms   42.137 ms   35.023 ms
10  216.239.43.30  55.215 ms   45.004 ms   55.549 ms
11  209.85.249.129  47.437 ms   56.409 ms nf-in-f104.google.com (64.233.183.104)  54.742 ms

It seems that I have one more entry in the IP routing table...
May it be related to the problem somehow?

I tried to ping this ip from the laptop, but got the message:
Do you want to ping broadcast? Then -b

A traceroute resulted in:
traceroute to 82.77.96.128 (82.77.96.128), 30 hops max, 40 byte packets
Unable to connect to 82.77.96.128: Permission denied

Do you need anything else?

Cheers,
don

---

### Post by lloyd_b on 2007-04-25
Unfortunately, the info from the SUSE box doesn't really help much - it's getting a completely different set of config parameters than the Ubuntu box:

Ubuntu: IP 10.106.89,239, Gateway 10.160.0.1
SUSE: IP 82.77.96.231 Gateway 82.77.96.129

The 82.77.x.x address is a valid "global" IP address - it can be used without the need for NAT (Network Address Translation).  The 10.106.x.x is a restricted IP address - it can NOT be used to access the internet without NAT/Proxying.  The fact that one machine gets the global address, while the other gets a local address, is rather odd.

I'm not going to be able to solve this one.  What I *think* is happening is that your cable modem/router is correctly providing the Ubuntu box with a good local address, but is failing to  provide NAT services, so the Ubuntu box can't get out.  The traceroutes from both boxes clearly show that the packets are reaching the same first router (86.127.41.1), but the packets from the Ubuntu box never get any farther than that.

So it is a routing issue, but not with the Ubuntu box - the problem lies with that first router.  It may be as simple as going into the cable modem/router configuration and enabling NAT, or there may be a more complex solution required.  I would suggest you take it up with your ISP's technical support - hopefully they can provide you with the specific instructions you need.

Sorry I have to say "I can't help you", but the issue is not with Ubuntu - it lies elsewhere in the network.

Lloyd B.

---

### Post by smurakozi on 2007-05-08
Hi Lloyd,

Finally I could solve the problem based on a tip coming from the ubuntu forums. 
The problem was caused by my ISP, as it locked my net access to the MAC address of my laptop. 
All I had to do is to use my the MAC address of my laptop on the desktop machine too, and it works fine now.

Thanks a lot for your help,
don

---

