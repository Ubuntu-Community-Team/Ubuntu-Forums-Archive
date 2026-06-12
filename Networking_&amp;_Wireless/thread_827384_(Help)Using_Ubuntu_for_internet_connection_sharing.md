---
title: "(Help)Using Ubuntu for internet connection sharing DHCP not working"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Malh on 2008-06-12
I currently have a server running 8.04 hooked directly into a fiber modem with working internet.  I have eth1 hooked to a series of switches that have 20-30 PCs/Macs hooked to them.  I'm using Firestarter and dhcp3-server to share the internet connection of the server with the rest of the network, but when I repair my internet connection on the PCs or the Macs, the server will not assign it an ip address.  What am I doing wrong?

---

### Post by superprash2003 on 2008-06-12
have you selected the right network adapter to share the internet connection to?

---

### Post by Kalibur on 2008-06-13
> **Malh said:**
> I currently have a server running 8.04 hooked directly into a fiber modem with working internet.  I have eth1 hooked to a series of switches that have 20-30 PCs/Macs hooked to them.  I'm using Firestarter and dhcp3-server to share the internet connection of the server with the rest of the network, but when I repair my internet connection on the PCs or the Macs, the server will not assign it an ip address.  What am I doing wrong?

In addition to Firestarter install a DHCP GUI called GDHCPD to configure your scopes getaways and DNS info its easy to use and has sufficient help.  Thats what I use and it works fine with ubuntu, Windows clients and have not tried Mac clients.

ignore the section below its a problem that comes up with misconfiguration on routers IP address.  So bottom line this works and is way to go.


*if u misconfigure routers ip the following happens*
Now my problem is it ubuntu clients dont connect to the internet through my server even though windows clients work perfectly.  A few points to note about my situation.
1 - the ubuntu clients get the ip address, DNS:confused: and getaway address successfully so I dhcp is passing and assigning the configurations.  But cant figure out why they dont connect to the internet.
2 - the ubuntu clients can connect in connected directly to my router
3 - My server is hardy 64 bit using GDHCPD firestarter and webmin
4 - Am using two NIC one for internet and one for LAN
5 - my switch is a netgear four port wireless router, i have disabled its dhcp and router functions. Wireless clients work fine, wireless access internet using ubuntu not tested.

---

