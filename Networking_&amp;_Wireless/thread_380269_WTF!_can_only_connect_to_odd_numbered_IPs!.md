---
title: "WTF! can only connect to odd numbered IPs!"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by hackeron on 2007-03-09
I have a truly bizarre problem, I can connect to: 217.10.79.23 but not to 217.10.79.28 -- Same mask, same network but somehow if the IP address ends with an even number, I can't connect to it.

Same goes for these:

can't:
217.10.79.28 [www.sipgate.co.uk](www.sipgate.co.uk)
66.35.250.150 slashdot.org
64.191.203.30 digg.com
85.234.146.50 my-bulldog-hell.co.uk

can:
217.10.79.23 sipgate.co.uk (this is a sip server, not the webpage)
64.233.167.99 google.com
72.14.205.83 gmail.com
66.180.174.35 distrowatch.org

Another clincher is if I restart my internet connection (PPPoA with bulldog) and get an IP address ending with an odd number (e.g. 87.74.78.35) then I can't connect to anything at all.

I have been doing traceroutes and I always reach the gateway but only reach the internet if the IP ends with an off number.

I think my ISP is responsible but they can't find a problem in almost 3 days so far...

Anyone seen something like this before and knows what could the problem be?

---

### Post by lloyd_b on 2007-03-09
Never seen this one before, but I can think of a possibility.  Just to clarify: You are saying that "traceroute" will ALWAYS reach the gateway, but will NEVER get anything after that if the IP address is an odd number?

If so, my bet would be on something screwy with the gateway router (very possibly a hardware issue).  Is this a new setup, or did it work correctly once and only recently began this behaviour?

Lloyd B.

---

### Post by melancholeric on 2007-03-09
One temporary workaround might be to find and use a transparent proxy you can connect to until you get it resolved.

---

### Post by hackeron on 2007-03-09
> **lloyd_b said:**
> Never seen this one before, but I can think of a possibility.  Just to clarify: You are saying that "traceroute" will ALWAYS reach the gateway, but will NEVER get anything after that if the IP address is an odd number?

If so, my bet would be on something screwy with the gateway router (very possibly a hardware issue).  Is this a new setup, or did it work correctly once and only recently began this behaviour?

Lloyd B.

Yes, I always reach the gateway, but I guess that's expected as I can ping it, but now something even stranger -  I've just reconnected and got an IP address ending with an odd number 87.74.78.11 and now I can only reach IP addresses ending with an even number but not those ending with an odd number.

So it looks like if my IP ends with an even number, I can only connect to IP addresses ending with an odd number and vice versa though sometimes getting an IP ending with an odd number means I can't reach anything.

I've had this connection for about 6 months and I only started having this problem early morning yesterday.

---

### Post by lloyd_b on 2007-03-09
> Yes, I always reach the gateway, but I guess that's expected as I can ping it, but now something even stranger - I've just reconnected and got an IP address ending with an odd number 87.74.78.11 and now I can only reach IP addresses ending with an even number but not those ending with an odd number.

So it looks like if my IP ends with an even number, I can only connect to IP addresses ending with an odd number and vice versa though sometimes getting an IP ending with an odd number means I can't reach anything.

I've had this connection for about 6 months and I only started having this problem early morning yesterday

If you can always reach the gateway, then it's unlikely to be a problem with your machine.  But let's take a look at the configuration anyway (never hurts to double check these things).

Could you run the following command in a terminal window, and post the results?
```
ifconfig
route -n

```

Another question: if you try pinging one of those inaccessible IP's, what message does ping display ("Host Unreachable", "Network Unreachable", etc)?

Lloyd B.

---

### Post by hackeron on 2007-03-09
> **lloyd_b said:**
> If you can always reach the gateway, then it's unlikely to be a problem with your machine.  But let's take a look at the configuration anyway (never hurts to double check these things).

Could you run the following command in a terminal window, and post the results?
```
ifconfig
route -n

```

Another question: if you try pinging one of those inaccessible IP's, what message does ping display ("Host Unreachable", "Network Unreachable", etc)?

Lloyd B.

```

server ~ # ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:40:63:D4:E2:A0  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113377995 (108.1 Mb)  TX bytes:159403783 (152.0 Mb)
          Interrupt:12 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13752 (13.4 Kb)  TX bytes:13752 (13.4 Kb)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:87.74.79.74  P-t-P:83.146.18.123  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:45973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:41499992 (39.5 Mb)  TX bytes:25853715 (24.6 Mb)

server ~ # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.146.18.123   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         83.146.18.123   0.0.0.0         UG    0      0        0 ppp0

server ~ # ping slashdot.org
PING slashdot.org (66.35.250.150) 56(84) bytes of data.
<ctrl+c>
--- slashdot.org ping statistics ---
173 packets transmitted, 0 received, 100% packet loss, time 172002ms

server ~ # ping google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=239 time=122 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=239 time=121 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=239 time=151 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=239 time=211 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=5 ttl=239 time=172 ms
<ctrl+c>
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 121.032/155.886/211.625/33.926 ms

```

---

### Post by lloyd_b on 2007-03-09
Okay, nothing jumped out at me from that info. 

I'm assuming that the gateway (83.146.18.123) is a router at the ISP.  From what I can tell, the problem lies either with that router, or possibly with the next router in the chain from there.

In short - the only thing I can suggest is another phone call to your ISP.  

Lloyd B.

---

### Post by hackeron on 2007-03-09
> **lloyd_b said:**
> Okay, nothing jumped out at me from that info. 

I'm assuming that the gateway (83.146.18.123) is a router at the ISP.  From what I can tell, the problem lies either with that router, or possibly with the next router in the chain from there.

In short - the only thing I can suggest is another phone call to your ISP.  

Lloyd B.

Looks like it - that is pretty strange though, I worked with ISPs before and I know balancing techniques such as round robin per packet or per destination port or per group of hosts , but to route the connection based on if the 4th number of the IP is odd or even, that's truly wtf.

Another thing is I looked at the log for the past 6 months and I've always used this gateway and my IP has always been 87.74.7{8,9}.* so I can't really detect any changes from this end to cause this, so I guess all evidence points to the ISP, but 2 days after phoning them up about it 2-3 times a day, they still can't find a problem.

Guess I'll order 1W amplifier for my wireless adapter, hook up a large panel antenna and hijack someone's wireless a couple of miles away until this is fixed :)

---

### Post by Mr. C. on 2007-03-09
It could be that the router has done a bit-flip on the netmask.

Try power cycling your modem/router(s).

If that corrects the problem, it could be bad hardware.

MrC

---

### Post by shortcut on 2007-05-21
Make sure your switch isn't configured for TRUNKING mode.

Some of the netgears behave oddly like this when a single PC is plugged into a port configured as a TRUNK port.

-S

---

### Post by aanvals on 2008-02-11
We had the same problem...It has to do with NIC teaming on the servers, and improper TCP/IP stack implementation on certain devices.  When traffic comes from the primary NIC of a team, it comes out with the MAC address of the team in the packet header.  However, when traffic originates from the secondary NIC, the header contains the MAC address of the 2nd NIC rather than that of the team.  This behavior is by design, and is part of the IEEE standard.  Unfortunately, some devices, such as (in this case) our UPS’s, and some printers, don’t properly handle this sort of thing, so they don’t respond properly.

---

### Post by netztier on 2008-02-11
A possibly misconfigured bond is a good hint, agreed.

> **aanvals said:**
> When traffic comes from the primary NIC of a team, it comes out with the MAC address of the team in the packet header.  However, when traffic originates from the secondary NIC, the header contains the MAC address of the 2nd NIC rather than that of the team.  [COLOR="Red"]This behavior is by design, and is part of the IEEE standard[/COLOR].  

However I'd rather doubt that the behaviour you describe is part of the IEEE design (could you quote us on this?). After all, it would cause chaos with the ARP caches of devices on the same subnet.

I'd rather call it the bug: NIC bonding not properly implemented - if a frame leaves *any* of the enslaved NICs, it must contain the *same* Layer2 address (read MAC address) for a given Layer3 address (read: IP address).

The only (well, as far as I know) exemption of this rule is Linux' bonding **mode 6**, where the driver makes sure that outgoing ARP replies use the actual address of the NIC they are using to exit the system. The ARP replies are being distributed evenly amongst the NIC team members, so that there is some load distribution. Such a setup can be used if there's many "clients" and one "server" on the same subnet, so you can get some receive load distribution.

It's bondig** mode 4** that  follows IEEE 802.3ad "Dynamic Link Aggregation" and requires the LAN switch to be configured accordingly.

regards

Marc

---

### Post by The Cog on 2008-02-11
That thread was 9 months old. In case you hadn't realised. I wonder if it ever got solved.

---

