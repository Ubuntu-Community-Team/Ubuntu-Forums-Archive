---
title: "mac traceroute?"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by rakku-toki telkio-kuuni on 2007-06-18
Does anybody know how to perform a route tracing on a network where some devices don't have an IP address?  In other words, is there a way to "traceroute" by mac address instead of IP address - or, at least, supposing that the last devices do have an IP but not some of the hops in between?

I couldn't find any program to do it so far...

Any answer is welcome.
Thank you :)

---

### Post by ReapingWildOats on 2007-06-21
Yeah, I am having a very similar problem.   I have a wireless router blocking my utorrent ports and I want to set port forwarding on it.  I have a mac address for it but can't connect to it through the browser to mess with the settings.  I dont even know if I can get an ip addy from a mac addy.  any clues?

---

### Post by spd106 on 2007-06-21
AFAIK you can't ping mac addresses, it just doesn't make any sense.

You can try pinging the broadcast address and see if anyone replies.
i.e. if you are on a network with address 192.168.0.x and mask 255.255.255.0
```
sudo ping -b 192.168.0.255
```

If they are IPv6 capable then the standard multicast address this might work as well (I know ubuntu responds, though I don't know why). You can then extract the mac address from the IPv6 addresses.
```
ping6 -I eth0 ff02::01
```

Arping can be used to match mac address to IP address via arp packets, you need to install it from the repos though, universe I think. The arp table is also useful as a mac address source. So is running wireshark on a broadcast medium such as wireless or an old hub based network (not switched).

YMMV

---

### Post by rakku-toki telkio-kuuni on 2007-06-25
Late reply, there was a big holiday here :)

> **spd106 said:**
> AFAIK you can't ping mac addresses, it just doesn't make any sense.

Yes, I know. But as far as switches with no ip can operate in a network, I suppose there should be a way to "ping" them.

> You can try pinging the broadcast address and see if anyone replies. (...) Arping can be used to match mac address to IP address via arp packets

But AFAIK most of the devices won't reply to broadcast packets. Besides, this would only work inside the local subnet...
And for some strange reason if I try to install arping, my network applet (KNetworkManager) will be uninstalled.

On the other hand, this can work for you, ReapingWildOats. If it doesn't, you'll need to get a copy of you router's manual, or call the manufacturers.

---

### Post by netztier on 2007-06-25
> **rakku-toki telkio-kuuni said:**
> 
Yes, I know. But as far as switches with no ip can operate in a network, I suppose there should be a way to "ping" them.

There isn't. 

Switches operate by MAC addresses and are blind to the payload ethernet frames carry. No switch I know of has any "echo" service running that would reflect an incoming packet back to the sender.

If any switch in the path doesn't know where to send the packet, it won't send any form of "unreachable" reply (like routers can be configured to do), but it will do what switches always do with frames that contain unknown destination MAC addresses: flood them out of all ports (belonging to the same VLAN). Any form of traceroute however depends on some entity sending back a "unreachable" message.

Switches have internal tables matching (destination)-MAC addresses to ports, so they know out which port they have to send a particular ethernet frame.

They all learn and populate these tables individually, by observing the source MAC addresses of frames entering each port. There is no "routing" protocol (BGP, OSPF, EIGRP, IS-IS) as with IP; Switches don't exchange their tables with their neighbors. There's actually no need to. We're at ISO/OSI layer 2 here: Local Link, there is no interest to see things "end-to-end".

If you have managed switches and you can log into them, you can manually "trace" the route to the MAC address you're interested in by logging into each switch along the path and inspecting the MAC-tables, then logging in to the switch that's connected to the port you've just seen in the first's table.

Some network management tools offer a graphical "MAC traceroute" by collecting the MAC table's contents via SNMP and then doing the analysis "offline", so to speak - but these are $$$ and most often not free.

The safest bet to check if a particular MAC-address is alive is to RARP for it - but you'll only get an answer if some deamon on that remote system is answering the RARP request. If you know the IP address of the device you're wondering about, ARP for it's MAC address and see if it shows up in your local ARP cache (**arp -a**). 


best regards

Marc

---

### Post by rakku-toki telkio-kuuni on 2007-06-26
Oh. Ok, Marc, than you very much. 

I guess there's not much left in this this case, only ARP in the local subnet or the "manual trace" you said.

There is also Cheops and Cheops-ng, I don't think they operate via SNMP, but AFAIK they don't recognize Layer 2 devices. Besides, I haven't tested them, and they aren't under development anymore...

---

