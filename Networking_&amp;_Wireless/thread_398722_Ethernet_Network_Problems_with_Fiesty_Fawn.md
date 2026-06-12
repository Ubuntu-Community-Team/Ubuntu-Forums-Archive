---
title: "Ethernet Network Problems with Fiesty Fawn"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by coolcalt on 2007-04-01
Hi all, i just purchased an Intel Core 2 Duo Processort E6300 and installed it in an Intel DQ965gf motherboard.  I have a generic network card installed in it as well as the onboard network card.  The motherboard has one IDE chain, to which I have an 80G Maxtor attached for the filesystem

I tried all day yesterday to get Edgy installed on it, but it was failing.  We figured out that the kernel in edgy didn't support my IDE drives so I got the Fielsty beta.  Its all installed and boots in seconds, but I don't have any networks, even though the live cd had network when I was installing it.

I looked in the logs and seen 

ipv6 : dissagrees about version of symbol structure.

both cards are in the network control app, and are set for DHCP, but are not getting an address assigned.

I'm guessing its not really worthwhile to set a manual ip and connect through my linksys router.   

I'm off to get a KVM switch so I can use both my old computer and this new one at the same time, any comments appreciated.

---

### Post by zvacet on 2007-04-01
Did Edgy recognized your modem?system>administration>network settings>highlight your modem>properties>choose type of connection(static,DHCP)>chek upper left box>close>DNS tab>replace existing address with your nameserver>close
```
pppoeconf
```

---

### Post by coolcalt on 2007-04-01
Modem??!  Who uses those anymore?

My problem seems to be that DHCP isn't working.  I tried setting both my ethernet cards to a static ip and connecting to my local network, but they don't pick up the (DHCP address from my cable modem, so unless i reserect my router, i can't get on the internet with the new computer
.

---

### Post by Psquared on 2007-04-22
> **coolcalt said:**
> Modem??!  Who uses those anymore?

My problem seems to be that DHCP isn't working.  I tried setting both my ethernet cards to a static ip and connecting to my local network, but they don't pick up the (DHCP address from my cable modem, so unless i reserect my router, i can't get on the internet with the new computer
.

Why would the router work when the cable modem won't by itself? From what I have read this is not a DHCP problem, but rather a kernel problem with Fiesty. I've got several Live CDs I am going to try them all to eliminate a bad NIC card. If I find one that works I'll  have to switch to another distro because Fiesty is just not cooperating on the networking issue. I can't believe they would release a version that would kill so many ethernet connections. Seems like a little more testing would be in order.

---

