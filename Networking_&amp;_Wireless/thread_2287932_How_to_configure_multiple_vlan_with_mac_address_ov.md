---
title: "How to configure multiple vlan with mac address over a single ethernet interface?"
date: 2015-07-23
forum: Networking &amp; Wireless
---

### Post by acerbuntu on 2015-07-23
Hi Guys [IMG]http://forums.debian.net/images/smilies/icon_biggrin.gif[/IMG] 

I want to configure multiple virtual ethernet interfaces over a single physical ethernet interface (eth0) and for each virtual interface the MAC address must be unique and the IP address must be Static.Finally all the virtual interfaces must be able to communicate both internally and externally and the traffic should be captured using wireshark.

I need to have such kind of setup to communicate devices individually using one physical ethernet device. 

Could you please guys give me a good step by step guide in doing this. Because I was fiddling with few kernel modules like MACVLAN and MACVTAP and successfully enabled those modules and rebuild kernel. Using macvlan and macvtap I can configure virtual interfaces with unique mac address and static IPs but while capturing packets using wireshark interfaces behave weirdly.

For example say on HOST machine I have 1 physical interface and created 3 virtual interfaces as shown below.

Interfaces :

eth0 (physical ethernet interface)
IP: 192.168.A.A
MAC: aa:aa:aa:aa:aa:aa

veth0(Virtual Interface 1)
IP:192.168.B.B
MAC: bb:bb:bb:bb:bb:bb

veth1(Virtual Interface 2)
IP:192.168.C.C
MAC:cc:cc:cc:cc:cc:cc

veth2(Virtual Interface 3)
IP: 192.168.D.D
MAC: dd:dd:dd:dd:dd:dd

Fisrt from above interfaces I started pinging eth0 internally from host machine in which it worked as usually.

Second I did same externally from other machine which is connected to the same network of Host machine, and this did work as usually.

Third I pinged first virtual interface veth0 both internally and externally and this also works and after that I did check source and destination MAC address using wireshark tool-where both showed up there respective MAC address.

Now triggers the issue, where I pinged second virtual interface same like I did for first one, but this time ping was success and where as in wireshark tool the MAC address for veth0 is picked by veth1. This is where I got stuck and this issue happened for all the remaining virtual interfaces.
I couldn't see any virtual interface showing their respective MAC address, as of the remaining except the first virtual interface has been picking the first veth0 mac address.

[IMG]http://forums.debian.net/images/smilies/icon_question.gif[/IMG] So I'm still not sure what I've done wrong. But I'm not geek in linux or networking. 

Please guys if you have any working plan then that will be a big treat.

Many Thanks,
acerbuntu [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]

---

### Post by acerbuntu on 2015-07-28
:frown:

bump !!!

Guys anyone please...

Not even one reply !!!

---

