---
title: "Gateway problem ?"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by A.I. BOT on 2007-04-20
I just installed XUbuntu Feisty today. Setup PPPoE with pppoeconf. I can connect to the internet fine. But when I need to download server lists (on things like some games) they all fail. I dont have any firewalls installed that I know of ... but FrostWire says it detects one.

Could this be a router problem or something? It was working fine in Edgy. I dont seem to have a gateway address either ...

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
142.166.182.37  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

Thanks :)

---

### Post by bnuytten on 2007-04-21
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
142.166.182.37  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

I am not very familiar with PPPoE or Frostwire. This line is normal and is the route to a network directly attached to your computer, hence there is no gateway (0.0.0.0). You probably have an IP address like 142.166.182.x.

You will be able to ping other hosts in 142.166.182.x (depending on your subnet mask) but since you are missing a default route you are not able to access other networks like the Internet. A default route would look like this. I just guessed the gateway based on your config so it probably won't work if you just add this route ;-)
```
0.0.0.0         142.166.182.1    0.0.0.0         UG    0      0        0 ppp0
```

What goes wrong in your case? Once you established a PPP connection you should receive an IP address from the provider's DHCP server. That DHCP server is also responsible for giving you the necessary routes (including the default route). Check that you have DHCP enabled for your dial-in interface...

PS: most providers use DHCP but in some rare cases (fixed IP e.a.) you have to config your IP,route manually

---

