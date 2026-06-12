---
title: "Debugging dhclient hanging within an LXC"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by srhadden on 2013-09-05
I have a server daemon which needs virtual IPs running within an LXC container.  This is how it has been working for me.

1. Create the macvlan

ip li add link eth0 macvlan1 address 88:88:1a:23:3e:c2 type macvlan

dhclient macvlan1

The mac-address is a randomly generated one.

Normally this works, but after some time something happened to my machine and now when I run dhclient frmo within the LXC it doesn't work.  Instead it just truns DHCPDISCOVER over and over again.

I do believe that dnsmasq is what dhclient is trying to access.  Because even though my macine may have a LAN address, all the IPs for the LXCs are local addresses to my machine such as 172.16.17.X.  Normally when I run dhclient on the macvlan I get an IP assigned to that virtual interface such as 172.16.17.200.

The dnsmasq process is set to list on 172.16.17.1.  I have compared a working machine with this broke machine and can't figure out the difference.

How could I go about debugging this? .  Thanks for any help

---

