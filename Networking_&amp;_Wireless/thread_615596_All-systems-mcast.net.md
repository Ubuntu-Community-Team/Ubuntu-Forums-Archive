---
title: "All-systems-mcast.net"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by paninero on 2007-11-17
I have been poking around with etherape, and I am a little confused about mcast, and the benefit for me as a home user.  I see a fair amount of chatter to ALL-SYSTEMS-MCAST.NET, and assorted IGMP traffic.  Now I have read a little, most of which is beyond me at this time, but basically my understanding it is say another layer of communication on top of my TCP communication that is brokering the best way to get information to me.

However, I don't like using things i don't understand to this large of a degree, and really after reading I see little benefit to me except maybe a little fast streaming from websites, so can someone please tell me some of the following.

First how can I remove mcast from the core Ubuntu install.  I know on Gentoo for example we could set a flag and leave it out of the compiles.

Second, I know I can block this in iptables, but I am curious what I might break, is there any packages that depend on this mcast.  And does anyone know why  ALL-SYSTEMS-MCAST.NET is the destination of the traffic, as I see there is no actual domain by that name.

And finally does anyone know why this is a core feature of Ubuntu, and who has made the decision to participate in the MBONE, whatever that is, by default.

Thanks.

---

### Post by DataMonSTAR on 2008-01-06
I'm using Ubuntu for the first time and just connected to the net and immedietly noticed the same. I'd like to know these answers as well if they haven't been answered already somewhere else. Thanks.

---

### Post by netztier on 2008-01-06
> **paninero said:**
> 
First how can I remove mcast from the core Ubuntu install.  I know on Gentoo for example we could set a flag and leave it out of the compiles.


I suggest to leave it in, by all means. ALL-SYSTEMS.MCAST.NET translates to 224.0.0.1. An IP packet sent to this group address will reach all systems on your subnet, and that is this address' purpose: to be able to send a packet to all multicast-speakers on the local subnet. If a non-multicast-speaking system on the subnet receives the packet, it will silently discard it.

Similarly, there is the address 224.0.0.2 (ALL-ROUTERS.MCAST.NET) - as it's name implies, all mutlicast-speaking routers will "listen" to this address. 

There's a lot more of them. See this list for the well-known multicast addresses: [http://www.iana.org/assignments/multicast-addresses](http://www.iana.org/assignments/multicast-addresses)

As you can see from that list, 224.0.0.x is the "Local Network Control Block". All IP packets sent to 224.0.0.x addresses have this in common: they must not be forwarded beyond the local subnet. The TimeToLive field in their IP headers must be set to 1 by the sender; each router receiving it would have to decrease this value by one, and because this would result in value of 0, the packet would have to be discarded by the router.

**UPnP** and **avahi / bonjour** heavily rely on multicast to work - devices can discover each other easiliy and in a way that is a lot less intrusive than broadcasts. In addition to that, IPv6 needs multicasting to find routers, DHCP-Servers and other systems on the local subnet.

Another example: Printers from Hewlett-Packard are using Multicast addresses from the "Local Internetwork Control Block" (224.0.1.60), so printer discovery becomes a lot more comfortable, even across router boundaries as found in many enterprise networks.

I consider it a good idea by Ubuntu to activate multicast; a number of services like name resolution (ever tried to ping another neighboring unbuntu box or Mac by [FONT="Courier New"]ping <hostname>.local[/FONT]? that's multicast based avahi at work...), file sharing, music sharing can be comfortably persuaded to "just work" and eliminate the need for a local DNS (complex for non-geeks), WINS (yuck!), hosts files (prehistoric) or data-transfer-by-usb-stick (does not really scale well).

So if you are certain that your broadband router has multicast support switched off, there is no need to worry that any of this traffic will ever leak out to the internet. In order to participate in MBONE, your router would have to be specifically configured anyway.

best regards

Marc

---

