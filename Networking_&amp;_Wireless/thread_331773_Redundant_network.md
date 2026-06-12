---
title: "Redundant network"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-01-05
Hey Guys.

I would like to make my server secure on the network - so its online no matter what. 

I have Nagios installed on it - and it should be in a redundant network 
There´s 2 Nics - But from 2 different Lines out of the house. The meaning if the one switch etc fails - the other one takes over - but the servier should still have the same IP?? 

How do I do that? 
The problem is perhaps more a question of installking it - it have this INTEL DRIVER: 
[http://downloadcenter.intel.com/scripts-df-external/Detail_Desc.aspx?strState=LIVE&ProductID=820&DwnldID=2895&lang=eng](http://downloadcenter.intel.com/scripts-df-external/Detail_Desc.aspx?strState=LIVE&ProductID=820&DwnldID=2895&lang=eng)

But when I try to compile the driver I get the following error: 
Makefile:412: *** Linux kernel source not found. Stop.
make failed

How can I make this work ??? Normally I use Arch Linux at home but at my new work - they use Ubuntu on the servers ?? 

THanks 
P

---

### Post by netztier on 2007-01-05
> **Peque said:**
> 
How can I make this work ??? Normally I use Arch Linux at home but at my new work - they use Ubuntu on the servers ?? 


We'll need more information here, about what you intend to do. Do you want active/standby failover? Active/Active with load-balancing, only on the server or also on the internet access lines and the LAN(s) all of this is connected to?

If your requirement is "one IP address, two NICs", you have to use **bonding** in failover or outgoing-load-balanced mode and use two separate (but interconnected) LAN switches. That is not very difficult to configure, search the forums, there's already been posts about it. There's no need for special ethernet drivers for that.

Using two different Internet access lines will require using a dual-WAN port router like the Linksys RV042 or RV082, or similar devices from other vendors. This of course will then be a single point-of-failure device...

If you want to use multiple Internet access lines from your home without a single intermediate device: forget it, this is going down the enterprise class road, requiring advanced LAN and WAN techniques, including BGP routing with your ISPs etc. 

If you really require redundancy of advanced grade, host your equipment with some collocation provider who will take care of it. The provider will also be able to provide dual power sources and UPS protection etc., which are also things to consider when aiming for high-availability, which often does not come without some hefty price tag.


best regards

Marc

---

### Post by Peque on 2007-01-05
Hey Mark! 

I want Active/standby failover. 

The server is about to be placed in a big hosting center - where there is 2 seperate lines. 

So bonding would be the answer - Thougth i needed the driver - So thanks

---

### Post by netztier on 2007-01-05
> **Peque said:**
> Hey Mark! 

I want Active/standby failover. 

The server is about to be placed in a big hosting center - where there is 2 seperate lines. 

So bonding would be the answer - Thougth i needed the driver - So thanks

Ah, there we go. That's the most clever way to get good redundancy. Sorry for wrongly assuming you were trying this "at home".

Ask the hoster if you'll get the two LAN ports from different switches or if you'll be dual-connected to a single switch. Availble/feasible bonding modes will be different, depending on the setup you'll get. Basically there's two cases:

[LIST]
[*]same switch: all modes possible, ask the provider for a 802.3ad (LACP) bundle and configure mode 4
[*]different switches: modes 0-3, 5-6 are possible. 2 (balance-xor) or 5 (balance-tlb) are the ones that will provide load-balancing and fault tolerance. Mode 6 (balance-tlb) requires special knowledge about Layer 2 network topology and is not always applicable. **Mode 2** should work in all cases.
[/LIST]
See also this thread: "[Has anyone verified that bonding works in Ubuntu?]("http://www.ubuntuforums.org/showthread.php?t=283113&highlight=bonding")" and read the "[Linux Ethernet Bonding Driver HOWTO]("http://www.mjmwired.net/kernel/Documentation/networking/bonding.txt")" (modes are explained from line ~250) that is also linked in that thread somewhere; that should get you started.

best regards

Marc

---

### Post by Peque on 2007-01-08
Well - we get the lines totally seperated. 

So bonding is the answer - Thanks a lot for the helpfull answer!
THat's what its all about!!! 

EDIT:
After what I can tell - there´s no support in my kernel ?? 
I have installed ifenslave - and follow the links Marc gave - But it seems as the kernel 2.6.15 doesn't support the bonding. 
Is there a special packages for this or do I have to build my own kernel

Per

---

