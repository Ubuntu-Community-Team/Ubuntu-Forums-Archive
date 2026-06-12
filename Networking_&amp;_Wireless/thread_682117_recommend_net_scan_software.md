---
title: "recommend net scan software"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by rooster78383 on 2008-01-29
Can someone recommend a simple sw package that will scan my home network and display all devices? My router DHCP server will show devices that have dynamic IP addresses, but it's the devices with static IPs that I tend to lose track of.

Thanks.

R

---

### Post by ridetheteapot on 2008-01-29
sw package?

netdiscover should do the trick or just use nmap 192.168.0.0/24 (nmap will be better for identifing which computer is which but i guess youll need a least a port open, netdiscover will only show you mac addresses, but  that grabs arp packets).

---EDIT
nmap uses arp by default on local networks, so that should work fine even if your pcs are completely discreet, in most cases.

---

### Post by rooster78383 on 2008-01-29
I was thinking of something along the lines of LANsurveyor, which will do an auto-discovery based on SNMP and create a graphical map.

---

### Post by ridetheteapot on 2008-01-30
if you want graphical there is cheops-ng and also lanmap.
lanmap isn't that great at all.....
and cheops just uses nmap (for the most part) to do its discovery, but has the graphical aspect.
I dunno if either will suit your needs because neither seems to give me a accurate map of the network.

If graphics aren't necessary, netdiscover is still the simplest, and you can always change your macs to something more distinguishable. 

there is also nagios2 which is probably overkill (and requires an apache). i think bixdata will also get a map, but its also overkill, plus its proprietary (but its free if your network is small)

---

### Post by rooster78383 on 2008-02-01
Thanks for the recommendations. Cheops-ng worked fine for my needs - although a bit buggy. I was able to designate a host, scan the network, get a graphical map, and export the map to jpg. 

rooster

---

