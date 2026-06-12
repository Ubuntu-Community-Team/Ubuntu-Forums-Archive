---
title: "Partial winbind naming failure. Frustrating."
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Boelcke on 2006-11-08
OK. I've got two ubuntu PCs, one running Hoary, one running Dapper. Hoary has a printer on it, which I'm able to print to from either machine, thanks to CUPS.

In my CUPS /etc/cups/client.conf file on the Dapper box, I've got a line that says
```
ServerName: 192.168.1.100
```
which tends to point it at the Hoary box, which has the printer.  When the Hoary box is at that IP address, all is good.  Due to some newly added devices in my network, this doesn't always happen anymore.

I've installed winbind on both machines.
I've edited /etc/nsswitch.conf on both machines to contain
```
hosts: files dns wins
```
I can ping each box from the other using their IP addresses.

Here's the issue:
From the Hoary box, I can "ping dapperbox" and it works. When I try and "ping hoarybox" from the Dapper machine, I get a host not found error.

This is sad, because I really want to edit that client.conf file on my Dapper box to point to the Hoary PC using its name, not an ever-changing IP address.

When I check my Linksys router's DHCP clients page, both machines have their names appear (they didn't before I did the winbind thing).

My Linksys 4-port, wired router doesn't seem to have an option to simply associate a fixed LAN IP address to a given MAC address.

Please help!

---

### Post by Boelcke on 2006-11-09
Or, let me ask about a different solution.  If I can figure out how to make the Hoary PC (the one with the printer attached) have a static IP address from my router, I can simply refer to it with that unchanging IP address on my LAN.  How do I do that?

I've seen a few suggestions on this, but haven't been able to get it to work. Several sources indicate to go into /etc/network/interfaces and change the line

```
iface etho0 inet dhcp
```

to 

```
iface eth0 inet static
address 192.168.1.199   # or any last number I want, out of DHCP range
netmask 255.255.255.0
network 192.168.1.0     # not sure what to put here
broadcast 192.168.1.255 # not sure what to put here
gateway 192.168.1.254   # not sure what to put here
```

Since I don't understand what the last 3 lines are, I'm thinking that I don't have those right.

---

### Post by Boelcke on 2006-11-09
Okay, I'm talking to myself here, but hopefully this answer will help someone else.  ;)

I solved my problem by having the hoard PC (the one with the printer attached) set to a static IP address within my LAN.  I did that by deleting the line in /etc/network/interfaces mentioned above, and adding this:

```
iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
gateway 192.168.1.1
```

The gateway is where your router is located at.

I didn't seem to need the network or broadcast lines.

The thing that confused me for a while is that, with my Linksys BEFSR41, it has a page that shows the DHCP clients that are attached.  That listing is apparently incorrect sometimes, because now it doesn't show my two linux clients (just the attached TiVo).  When I do "ifconfig" the IP address shows up correctly.  Also, I can ping each box from the other, using IPs.  I wonder why that isn't showing up correctly, but everything else seems to be working.

---

