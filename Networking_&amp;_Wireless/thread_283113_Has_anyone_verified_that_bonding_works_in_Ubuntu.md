---
title: "Has anyone verified that bonding works in Ubuntu?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by BrianK on 2006-10-23
I've recently built up 4 file servers all using nearly identical hardware.  On one of them, I installed Suse, the other three got Ubuntu.  on the Ubuntu machines, if I run iptraf & monitor all interfaces, I only see one interface of four doing anything (there's actually 6 interfaces, but only four of them are configured for the bond). On the Suse machine, all four interfaces get pretty good throughput.

So something's wrong... it's either my config, Ubuntu's iptraf (which I'm pretty sure is not the case becasue I just downloaded and compiled from the latest iptraf source), or something with Ubuntu's bonding module or ifenslave program.

Can someone else verify, with iptraf, that more than one interface in your bond is working?  It's easiest to see by simply running iptraf (available via Synaptic/apt*) & using option 2 which is "Genearl Interface Statistics".

I'm happy to post my config here if anyone's interested.  I'm using 802.3ad for the bonding module.

---

### Post by abshnasko on 2006-10-23
I've gotten it to work, but not exactly how I want it to... I've created the bond0 interface and have been able to access the internet. What I have not been able to do, however, is get it to let me use both cards at once. bonding mode 0 should do this, however I am still getting the throughput of only one of my ethernet cards.

So yes I can confirm that it works, but can anyone help me with the problem I'm having?

---

### Post by BrianK on 2006-10-23
> **abshnasko said:**
> I've gotten it to work, but not exactly how I want it to... I've created the bond0 interface and have been able to access the internet. What I have not been able to do, however, is get it to let me use both cards at once. bonding mode 0 should do this, however I am still getting the throughput of only one of my ethernet cards.

So yes I can confirm that it works, but can anyone help me with the problem I'm having?
Well, that's no more confirmation than I have.  My bond works, but only one of the interfaces in the bond does anything... So it sounds like we are in the same boat.

---

### Post by abshnasko on 2006-10-27
I've read info in many places that say the bonded interfaces must be plugged into a switch that supports port bonding. I've got a linksys switch sitting here not doing anything, so I'm gonna plug into that and see what happens. Since we have it set up right, I'm guessing that could potentially be a problem we haven't addressed.

In my dorm there are two ports, presumably going into a sort of "switch" to connect me to the rest of the network. They are 10mbit ports... now that I think about it I wouldn't guess that they would give us the sort of freedom to tamper with the network in this way.

I'll let you know tomorrow how my new setup goes

---

### Post by netztier on 2006-10-27
> **abshnasko said:**
> I've read info in many places that say the bonded interfaces must be plugged into a switch that supports port bonding. I've got a linksys switch sitting here not doing anything, so I'm gonna plug into that and see what happens. 

This is almost true. The other half of the truth depends on what traffic direction you want the bonding to be effective.

[SIZE="3"]**Outgoing Traffic **[/SIZE]
If you have a server in the sense that it sends a lot more traffic than it receives, you want "outgoing" bonding and load-balancing.

This is the easy way, and can be done with any cheap unmanaged switch. It's just up to the server to decide which interface to send the datagram/packet/frame out of, using the same MAC address as source in all cases of course. As a server, you can't go around and use alternating MAC addresses for the same IP, this would wreak havoc in the other devices' ARP caches.

Basically this mode can be used in two ways:
[LIST]
[*]redundancy-only: one interface is active, the other is standby
[*]load-balanced:  traffic leaving the server is distributed among the active members of the channel bundle
[/LIST]

I have never configured a channel-bonding interface on Linux myself, I'm speaking as a networker here - you'll have to figure out how to configure this.

The **[COLOR="Red"]downside[/COLOR]** of this is that only one interface will ever be used for incoming traffic. When another device or the router in your LAN ARP-broadcasts for your IP, your server will have to know which MAC-Address to answer with, and that will be the interface that will be getting the incoming traffic.

The **[COLOR="Green"]upside[/COLOR]** of this is that you can have both your interfaces connected to different (but interconnected) switches, so if one switch fails, your server is still reachable.


[SIZE="3"]**Incoming Traffic**[/SIZE]
Now here things are getting more difficult. If you want your server to take advantage of multiple parallel links for incoming traffic (i.e. by having just one IP interface in one subnet, but multiple parallel ethernet links), you'll need an ethernet switch capable of link aggregation.

There's different ways to configure an ethernet bundle, of which some are proprietary, such as Cisco's (Fast/Gigabit)Etherchannel which is configured manually, Cisco's PAgP (Port Aggregation Protocol) [COLOR="Gray"](you can tell I'm a Cisco guy, can't you?)[/COLOR], or the IEEE 802.3ad standard LACP (Link Aggregation Control Protocol). Of these, I assume that LACP is best supported in Linux.

Whatever mechanism you choose, your switch has to support it, and both ends must agree on which protocol to use, and all member interfaces must be of the same speed and duplex settings.

[INDENT][COLOR="RoyalBlue"][I]Edit: This is not quite true; the ethernet switch doesn't have to support ethernet bundling in all cases. In: [http://www.mjmwired.net/kernel/Documentation/networking/bonding.txt]("http://www.mjmwired.net/kernel/Documentation/networking/bonding.txt"), we find information about bonding mode **balance-alb** or **6**. 

```
balance-alb or 6

Adaptive load balancing: includes balance-tlb plus
receive load balancing (rlb) for IPV4 traffic, and
does not require any special switch support.

```


Whith this mode, you can influence incoming load-balancing (although I'd rather call it load-sharing), by craftig individual ARP replies for each peer. Originally, the normal ARP replies have the MAC source address of the bonding interface. In mode 6, the driver overwrites it with the unique MAC-address of one of the bundle member NICs - the NIC that will get the incoming traffic from that peer.

Like this, you can ensure that different peers use different MAC addresses for the same server. Still, the same restriction of **n**x100Mbps vs **n**00Mpbs applies, as explained below. The other restriction is that it only works with some NIC/driver combination and that it is currently limited to IPv4.[/I][/COLOR][/INDENT]





**[SIZE="3"]Why don't I get 400Mbps over a 4-port-802.3ad link bundle?[/SIZE]**

In the sense of how a switch works, it will bundle up the member interfaces to a single interface and in it's internal forwarding rules, the bundle will be regarded as a single link. 

Now here comes the not-so-obvious part. Somehow, the switch or Server will have to determine which member link to use for a certain frame.

Traditionally, this is done by doing an XOR operation of the last "n" bits of the source and destination MAC addresses of the frame that is about to be sent over the link bundle.

If you have a 4-port-bundle, the last 2 bits of the MAC addresses are XORed, and the binary result (00, 01, 10, 11) will then be the number of the member link to use. For an 8-port-bundle, three bits are used.

More advanced multilayer switches can also use bits from the IP or TCP headers to XOR against each other. But since the switch *must* not assume that all ethernet frames contain IP packets (IPX/SPX, DECnet, anyone?), a switch should stick to MAC addresses unless configured otherwise.

So - let's assume the following case:

[LIST]
[*] Client 1Gbps, single NIC, connected to switch
[*] Server 4x100Mbps, bonded NICs in 802.3ad mode (mode 2, using xmit_hash_policy "layer 2"), connected to an 802.3ad port bundle on the same switch. 
[*] Switch uses 2bit-XOR to distribute load among the member ports
[*] Client **uploads** large file to the server.
[*] Observation: perfomance won't be any faster than with a single 100Mbps link.
[/LIST]

Each NIC involved has only one MAC address, and when the switch will calculate the XOR of their last 2 bits, the result will always be the same. Consequently, only one member link of the bundle will ever be used, and that is why iptraf or any other tool will report traffic on one interface only, which is limited to 100Mbps.

[COLOR="Blue"][B]In other words:
If you bundle [COLOR="Red"]n[/COLOR] 100Mbps links, you don't get one [COLOR="red"]n[/COLOR]00Mps highspeed link, but [COLOR="red"]n[/COLOR] times a 100Mbps link. It's like adding more lanes to a motorway but keeping the same speed limit.

If you want a bundle to have a performance-effect, you have to make sure that the communication flowing across it is one-to-many or many-to-many. One-to-one communication will not benefit from it.[/B][/COLOR]

regards

Marc

---

### Post by Akhran on 2006-10-27
I've the same problem too; one nic seems to be doing all the work and failover doesn't work.

One observation: assuming nicA is the one doing all the work, if I unplug nicA and do a 'route' command, the last route (default route) takes about 20s to show for the bond0 interface. If I unplug nicB and do a 'route' command, the entire routing table is shown almost instantly. Is that the norm?


> **BrianK said:**
> Well, that's no more confirmation than I have.  My bond works, but only one of the interfaces in the bond does anything... So it sounds like we are in the same boat.

---

### Post by netztier on 2006-10-27
> **Akhran said:**
> 

One observation: assuming nicA is the one doing all the work, if I unplug nicA and do a 'route' command, the last route (default route) takes about 20s to show for the bond0 interface. If I unplug nicB and do a 'route' command, the entire routing table is shown almost instantly. Is that the norm?

Try [FONT="Courier New"]**netstat -nr**[/FONT] instead of [FONT="Courier New"]**route**[/FONT]. The "n" flag disables nslookup during display - the routing table should show up instantly, in both cases.

regards

Marc

---

### Post by BrianK on 2006-10-27
> **netztier said:**
> 
**[SIZE="3"]Why don't I get 400Mbps over a 4-port-802.3ad link bundle?[/SIZE]**

Nice writeup Marc.

Let me disagree a little bit -

It *is* true that no single computer (other than the computer with the bond) will ever see more than single line speed, however, it is *not* true that the network as a whole will not see more than single line speed.  In other words, if I have 50 machines writing to a file server that has a 4-port 802.3ad bonded interface, the server should see a total input speed of 4 * single line speed (assuming , of course, that the MAC based hash doesn't somehow point all machines to one NIC - which is less probable thn hitting the lottery).  No single machine outside of the file server will see more than single line speed, but the server should.  *This* is what I'm not seeing in Ubuntu, but what I do, infact, see under Suse - at least as can be verified with IPtraf.

AFAIK, this is the whole point of 802.3ad.  If only one line ever worked, then bonding would only be useful for fail-over.

edit: re-reading your post, I don't think that any part of your post was incorrect, but let's change your example:

[LIST]
[*]Switch with some form of link aggregation across 4 ports
[*]Server connected to those 4 ports via 4 802.3ad bonded 1Gb/s NICs
[*]4 client machines with 1Gb/s NICs connected to the same switch
[/LIST]

Now This setup should see 4 * 1Gb/s (minus packet headers, latency, and such) on the server assuming the server's internals can keep up.  Each of the client machines should see a full 1Gb/s output - as if they were the only ones writing to the server at that one time.  *This* is what works under Suse, but not Ubuntu - at least as can be verified with IPtraf. ;)

---

### Post by Akhran on 2006-10-27
That works, but when nicB is unplugged instead of nicA, why is it that the routing table is displayed instantly with the 'route' command? If the 20s delay is due to name resolution, shouldn't nicA have the same problem too?

Thanks !

> **netztier said:**
> Try [FONT="Courier New"]**netstat -nr**[/FONT] instead of [FONT="Courier New"]**route**[/FONT]. The "n" flag disables nslookup during display - the routing table should show up instantly, in both cases.

regards

Marc

---

### Post by netztier on 2006-10-29
> **BrianK said:**
> 
Now This setup should see 4 * 1Gb/s (minus packet headers, latency, and such) on the server assuming the server's internals can keep up.  Each of the client machines should see a full 1Gb/s output - as if they were the only ones writing to the server at that one time.  *This* is what works under Suse, but not Ubuntu - at least as can be verified with IPtraf. ;)

Agreed. On the other hand, 4 x 1Gb/s is quite a hefty bit of throughput, that'll need some very decent storage and I/O performance :-)

Agreed also that the network as a whole will of course see more than "single link" throughput, if the switch's backplane (and where applicable the network backbone) actually supports it - not really a problem these days. 

Nonetheless, provided that the MAC-address XOR hashes really have four different results, the switch will distribute packet flow *from the clients to the server* evenly among the 4 member links.

If the bonding driver in the server also does the MAC-address hashing properly, it should do the same for the traffic flow *from server to clients*.

I could get my hands on some 802.3ad capable switches, but my home network lacks servers and NICs, so I can't really help any further here. 

Should there be reason to be suspicious about iptraf's output, one might want to try looking at the switch's port counters or I/O statistics for the 4 member ports to really see how traffic is distributed across the links. I'm positive that a switch that allows 802.3ad to be configured will also have port counters.

regards

Marc

---

### Post by BrianK on 2007-03-26
In case anyone comes across this post looking for answers, my problem was with my switch oddly enough.  Evidently, the Linksys SRW2024 does not do link aggregation correctly.  I recently ran out of room on the 24 port so I moved up to the 48 port Linksys (the SRW2048) - now the trunk works great - all interfaces seeing lots of activity.

---

