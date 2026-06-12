---
title: "What is a Mbit? How fast should my network go?"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-07-23
Help....going mental with figures.

How many KiloBytes (captial KB?) do you get from 1 Kilobit (lower case b in Kb)???

How fast is Ethernet and Fast Ethernet?  Am I correct in saying that they are 10Mbit and 100Mbit respectively?  As opposed to 10MByte/100MByte, which I had previously assumed.

If my logic is not completely in a different universe, this is how I work out how many KB I get when transferring files on a 100Mbit Fast Ethernet link:

100 Mbit x 1000 = 100,000 Kbit

100,000 Kbit x 1000 = 100,000,000 bits

## I assume that as were not working in base-2 yet, that Kilo still means "1000", but once we swap over to bytes then it's base-2 and therefore kilo = "1024"?

100,000,000 / 8 = 12,500,000 Bytes   ## 8 bits in a Byte

12,500,000 / 1024 = 12,207 KBytes

12,207 / 1024 = 11.9 MBytes
--------------------------------------------
100 Mbit = 11.9 MBytes per second.

Using the same logic...

10 Mbit = 1.2 MBytes/s
1 Mbit = 122 KBytes/s
54 Mbit = 6.4 MBytes/s


The reason I ask is that I run a laptop as a SSH server using Ubuntu 7.04 and I have a Linksys Gateway (WAG325N) running at 100Mbit on the 4 port ethernet switch.  The laptop has a gigabit ethernet card but obviously running at 100Mbit to the gateway.

My other laptop has 100Mbit ethernet also, Intel ICH7 chipset.  Both laptops have static IP addresses.

When I run scp to transfer a 200MB file to the server, scp reports that the transfer speed was 11.5MB/s, which ties in with how I calculated how many MB/s I get on 100Mbit link.

However, when I connect the laptop to the server using a cross-over cable, bypassing the router, then scp reports that the speed is 22MB/s on multiple transfers!!??  Does this indicate that the gateway is only running half-duplex, and that when I connect using cross-over cable it is running at full-duplex and is therefore twice the speed?  Or does this mean I have calculated my MB/s incorrectly for a 100Mbit LAN link?

If this does indicate that the gateway is running only half-duplex then how can I make it run at full-duplex.

For some reason, a 6GB TAR file was taking 1Hr to transfer, but if I worked things out correctly, then 6GB should take only 10 minutes!

That was a lot of questions...hope some network engineer can help me out!

---

### Post by dannyboy79 on 2007-07-23
Here's the conversions

1 kilobit = .125 kilobyte

1 megabit = .125 megabytes

1 gigabit = .125 gigabytes

So, if you have a 100megabit ethernet card, it theoretically can transfer at 12.5 megabytes per second BUT you're limited to a lot of things like overhead for the TCP/IP stack, the PCI bus runs 32bits per cycle and 33,000 cycles per second, so the max throughput of the bus is 1.056Gbps. So running a gigabit pci nic on a standard desktop the network traffic can completely saturate the pci bus. So any other pci cards using the same bus (sound cards, tv cards, etc) will lower your max network speed. This is why servers run 64bit pci bus and why new standards are coming out like pci-x which will double the speed of the bus, giving you a max throughput of 4.224Gbps. You toss 2-4 gigabit cards in there with teaming and NOW you've got some serious bandwidth. :D

I can tell you that I transfer over 100 Based T all the time using samba and I get anywhere between 6 and 8 megabytes per second. I can get almost 10 when using FTP, althought I am not sure why? It's possible that your router/switch is a bottleneck based on what you have informed me but remember, the switch within that has to process and tell the packets where to go based on the source and distination MAC addresses, so that takes time doesn't it? Are you sure that your router/switch supports Full Duplex?

---

### Post by finite9 on 2007-07-23
> **dannyboy79 said:**
> Here's the conversions

So, if you have a 100megabit ethernet card, it theoretically can transfer at 12.5 megabytes 


I did say that I can transfer at 11.5MBytes/s, so I guess that it is running at 100Mbit.

But I wonder why I consistently get 22MBytes/s when using a crossover cable?  Does this indicate the that it is running at full duplex and the router was not?

The router does say it supports full duplex, but there is no status page in the web interface to verify this.  How do I check if the ethernet card is connected using full duplex?  Is there a CLI tool like ifconfig that reports the link status?

---

### Post by gangolli on 2007-07-24
Install ethtool

> aptitude install ethtool 

Then run it as root with the name of your ethernet interface (you may need to replace eth0 accordingly):

> sudo ethtool eth0

This will tell you what the device advertises that it supports and what the current negotiated link rate and duplex are.

---

### Post by dannyboy79 on 2007-07-24
well that's for that interface only, not the ethernet port within your router. It sounds to me like your router does NOT support full duplex but your computers ethernet cards do.

---

### Post by gangolli on 2007-07-24
Yes, in this case, one should see via ethtool that the negotiated state is half duplex.

---

### Post by finite9 on 2007-07-26
I tested ethtool on the server and it reports that the link is full duplex.  This must mean that the routers port supports full duplex.  I have not tested the other client PC yet with a wired link to see if that also supports full duplex.

---

### Post by dannyboy79 on 2007-07-26
> **finite9 said:**
> I tested ethtool on the server and it reports that the link is full duplex.  This must mean that the routers port supports full duplex.  I have not tested the other client PC yet with a wired link to see if that also supports full duplex.

you need to read the negotiated state NOT just the link.

---

### Post by finite9 on 2007-07-26
> **dannyboy79 said:**
> you need to read the negotiated state NOT just the link.

```
sudandrew@K2:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
[COLOR="Red"]        Duplex: Full[/COLOR]
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

does this mean negotiated?  It's not in the supported or advertised list so I am assuming it is the actual link state right now.

---

### Post by dannyboy79 on 2007-07-26
> **finite9 said:**
> ```
sudandrew@K2:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
[COLOR="Red"]        Duplex: Full[/COLOR]
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

does this mean negotiated?  It's not in the supported or advertised list so I am assuming it is the actual link state right now.
well my inexperience with ethtool made me just agree with the previous guy who said that the negotiated state would be listed there but obviously it's not. I am not sure how to use ethtool to get the negotiated link between 2 ip's? Did you try to read the man pages? man ethtool
I can't help you anymore, sorry.

---

