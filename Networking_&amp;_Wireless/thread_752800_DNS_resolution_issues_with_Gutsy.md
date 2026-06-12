---
title: "DNS resolution issues with Gutsy"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Eynowd on 2008-04-12
I've been running Gutsy for a while on an old VIA box a friend of mine gave me. Until yesterday, it had been in a standalone mode, because the router was at the other end of the house and I couldn't get a spare wireless card to work.

Having moved house and finally getting my net connection back, I plugged the box directly into the router using a cable.

My windows boxes were able to surf the web quickly, given that my ADSL speed had been increased during the move. But when I went to try to use the Linux box, the connection speed was horrifically slow and would time out more often than not.

Initially, I thought it was due to a slow old box and all sorts of flash advertisements on the news webpage I was trying to load. So I decided to load the hosts file from [http://www.someonewhocares.org/hosts]("http://www.someonewhocares.org/hosts"), to block most of them out, the way it does on my windows machines. So, I added the details on that page to the bottom of the /etc/hosts file.

That didn't seem to fix the problem.

I did some hunting online, which indicated that it could well be an IPv6 issue. So, I followed the instructions on [this page]("http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html"), but it only seemed to make things worse. Where before I could at least *get* to a webpage, afterwards, I couldn't even get that far. It just kept timing out.

I tried rolling back most of the changes I had made (while still leaving the IPv6 disabled), but nothing seemed to work. I even removed the whole /etc/hosts file, but it doesn't seem to have made any difference.

If I do a "sudo ethtool eth0", I get the following:

```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes

```

if I do a "sudo ifconfig eth0", I get: 

```

eth0      Link encap:Ethernet  HWaddr 00:40:63:D3:1B:36  
          inet addr:192.168.0.150  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:774
          TX packets:967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27763 (27.1 KB)  TX bytes:96204 (93.9 KB)
          Interrupt:11 Base address:0xe800 

```

As I'm a complete Ubuntu noob, I'm completely at a loss at this point to figure out what's wrong with the machine and what I need to do to go about fixing it. 

Does anyone here have any suggestions on how I can get the machine to be able to find the internet successfully?

---

### Post by stream303 on 2008-04-12
> **Eynowd said:**
> Does anyone here have any suggestions on how I can get the machine to be able to find the internet successfully?

In regards to DNS issues, the easiest solution for me has always been to put my isp's primary and backup dns server addresses inside the router's setup page and then let the machines pick it up from there, rather than try to edit config files.  This helps bypass some of the windows-centric dns quirks our soho routers sometimes have.

I actually prefer using outside dns servers from
[http://www.opendns.com](http://www.opendns.com)

See the bottom right of the page for the addresses.  Perhaps putting your isp's addresses or those from say OpenDNS.com in your router will save some frustration...

---

