---
title: "dsl slow on ubuntu"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by seanbarman on 2008-04-08
Hi, just upgraded my connection to 20mb, but i am only getting 2mb download speeds under ubuntu, I am getting 18mb under windows, i have disabled ipv6 and pages load ok, just seems like my speeds are capped 50min for ubuntu iso

thanks

---

### Post by nixscripter on 2008-04-08
Sounds like a software problem.

FIrst of all, what network card are you using? If it's an ethernet connection, then check on what **ethtool** says about the card. It might be operating in a slower mode (for some reason).

Use ```
ifconfig
``` to determine which interface the card is, and then run ```
sudo ethtool **if-name**
``` to get the parameters.

---

### Post by seanbarman on 2008-04-09
ethtool shows

Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


ifconfig

eth1      Link encap:Ethernet  HWaddr 00:50:8D:B3:BA:A2  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:7644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8174135 (7.7 MB)  TX bytes:1890601 (1.8 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7786 (7.6 KB)  TX bytes:7786 (7.6 KB)

It is an onboard card on ABIT IP35-e motherboard. We are having same issue on an other pc which uses a different card to. Download speed seems capped, but is ok in Windows.

thanks for the reply.

Thanks for the reply.

---

### Post by nixscripter on 2008-04-10
> **seanbarman said:**
> ethtool shows

Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


And that was when you typed: ```
sudo ethtool eth1
``` right? If I'm right, try ```
sudo mii-tool
``` and post that. Please also put [ CODE ] blocks around the output to make it easier to read.

What I'm trying to do is determine the ethernet link speed. My guess is that, for some reason, it's negotiating a lower speed than it does under Windows.

> 
It is an onboard card on ABIT IP35-e motherboard. We are having same issue on an other pc which uses a different card to. Download speed seems capped, but is ok in Windows.


I figured it was a configuration problem, that makes it very likely.

---

### Post by Manasia on 2008-04-10
I am having the same problems as the other guy here are my stats. 


[ CODE ]
eth0      Link encap:Ethernet  HWaddr 00:50:2C:01:39:E6  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe01:39e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4261808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4238567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2005488990 (1.8 GB)  TX bytes:303900826 (289.8 MB)
          Interrupt:11 Base address:0xe800 


192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0



Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 70)
[ CODE ]

---

### Post by Manasia on 2008-04-10
I do notice the metric to the device is only 1000 and my card is set to 1500 could that be a problem?

---

### Post by Manasia on 2008-04-11
Anyone got any ideas about this?

---

### Post by freebeer on 2008-04-12
did you try turning off ipv6 in firefox?  (I'm assuming it's firefox related.)

in the address box of firefox, type "about:config" then search for "ipv6".  Set "disable ipv6" to "true"  (going by memory here, so my wording may be off a bit).

---

### Post by Manasia on 2008-04-12
> **freebeer said:**
> did you try turning off ipv6 in firefox?  (I'm assuming it's firefox related.)

in the address box of firefox, type "about:config" then search for "ipv6".  Set "disable ipv6" to "true"  (going by memory here, so my wording may be off a bit).

This is not really related to firefox, all my downloads in general, outside of firefox.

---

### Post by nixscripter on 2008-04-12
As I suggested to him, what happens when you run ```
sudo ethtool eth0
```?

and by the way, there is no space between the brackets and the word "code" in the forum tags; typo on my part.

---

### Post by Manasia on 2008-04-12
[CODE]
       
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

[CODE]

---

### Post by Manasia on 2008-04-12
oh yea man, how is Minnesota, I used to stay in ND and MN before I got here to ATL.

---

### Post by nixscripter on 2008-04-12
Most of the time, it's cold ;-)

As for the card, it looks like it's negotiating a high speed. Can you get any better speed connected to something else? It could just be a slow other end.

---

### Post by Manasia on 2008-04-12
Nah man, not nothing at all, i even checked the link on the dsl router and it is at 8MBPS down, but I am only getting like 732K down. My nic is on-board and it is old, I was thinking a new one might help. 

The line is also good, and on wireless I get faster download speeds.

---

### Post by seanbarman on 2008-04-13
Hi,

upgraded to hardy now,

everything is fine now

thanks.

---

### Post by Manasia on 2008-04-16
I upgraded to hardy and my **** is still slow. I am gonna buy a new NIC.

---

