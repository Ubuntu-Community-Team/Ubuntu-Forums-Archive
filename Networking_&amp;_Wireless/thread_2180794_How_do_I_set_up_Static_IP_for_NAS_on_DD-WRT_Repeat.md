---
title: "How do I set up Static IP for NAS on DD-WRT Repeater Router?"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by Casey_Friday on 2013-10-14
I'm running Ubuntu Server 12.04.3 on a NAS I just built.  Right now, it's plugged directly into the main Airport Extreme (5G) router in the house.  At the other end of the house - where I'd like to put the NAS - I've successfully set up a DD-WRT Repeater router that sends a strong WiFi signal for the back of the house.  I'd like to wire the NAS directly into this DD-WRT repeater router, but I'm not sure of the static IP settings needed.  Here are my current settings:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.100
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.0.1
    dns-nameservers 192.168.0.1 208.67.222.222
```

The Airport Extreme is at 192.168.**0**.1.  I've set up the DD-WRT repeater router to have an IP of 192.168.**1**.1.  When I move the NAS to the DD-WRT router, should I change 'gateway' to 192.168.**1**.1?  Do I also need to change the 'address' to 192.168.**1**.100?  And 'network' to 192.168.**1**.0?

It's a headless NAS, so I want to make sure I get the settings right before I unplug it and put it somewhere else.  Thanks!

---

### Post by scbingham on 2013-10-15
I don't think you should be creating another subnet at all, ie the 192.168.[COLOR=#ff0000]1[/COLOR].xxx network.

Your Airport Extreme is presumably the DHCP server, it will allocate addresses from within a certain range eg 192.168.0.[COLOR=#ff0000]100[/COLOR] to 192.168.0.[COLOR=#ff0000]254[/COLOR]. Check the router for exact details.
The bunch of addresses from 192.168.0.[COLOR=#ff0000]2[/COLOR] to 192.168.0.[COLOR=#ff0000]99 [/COLOR][COLOR=#000000]are available for you to allocate as static addresses for servers, printers, repeater routers etc.

So, get rid of any mention of 192.168.[/COLOR][COLOR=#ff0000]1[/COLOR][COLOR=#000000].xxx & also ensure the repeater router is not acting as a DHCP server.
Set your repeater router to be 192.168.0.2 & set a static ip for your NAS from within 192.168.0.3 to 192.168.0.99

Hope this helps[/COLOR]

---

