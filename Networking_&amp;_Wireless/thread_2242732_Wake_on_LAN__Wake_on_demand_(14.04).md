---
title: "Wake on LAN : Wake on demand (14.04)"
date: 2014-09-03
forum: Networking &amp; Wireless
---

### Post by talzia on 2014-09-03
For those trying to get Wake on LAN (WOL) to work with "Wake on Demand"..

Edit or create /etc/network/if-up.d/wol to contain the following:
```

#!/bin/bash
/sbin/ethtool -s eth0 wol ug

```
And make it executable (chmod +x /etc/network/if-up.d/wol)

This sets the eth0 WOL options to unicast & magic packet each time eth0 comes online..
(unicast apparently means directed at that specific network interface) 

**The powersave problem**
On Ubuntu 14.04 /usr/lib/pm-utils/sleep.d/00powersave somehow resets eth0 WOL options to just "p" (magic packet only) when the computer goes to sleep so I simply removed it..

**The ARP problem**
After a 30 second timeout computers forget which IP belongs to which MAC (physical) address.
Some network cards also allow waking up on ARP (ethtool -s eth0 wol uga) which should fix that the easy way..
If yours doesn't you can either enter it as a static mapping on your clients:
[LIST]
[*]Windows: arp -s 192.168.0.1 00-00-00-00-00-00 
[*]Linux: arp -s 192.168.0.1 00:00:00:00:00:00 
[/LIST]
(replace proper IP & corresponding MAC addresses)
Or use a proxy-arp on your router (dd-wrt apparently supports this) that will do the translating for your clients.

Anyways, i added a static ARP entry on my windows workstation..
When i boot up my workstation in the morning and it tries to access my samba shares on the server the server wakes up nicely..
That's about 200 euros saved each year for not having my server up 24/7

Hope this helps somebody else..

---

### Post by talzia on 2014-09-04
After a minimal reinstall, this time without network-manager installed with ubuntu-desktop, I noticed the WOL options were no longer properly set to "ug" after reboots..
It seems that (without network-manager?) the WOL options set in the /etc/network/if-up.d/wol script get overwritten by something else in a later stage.

I did not feel like installing network-manager just for this so I added the "/sbin/ethtool -s eth0 wol ug" line to /etc/rc.local and it works fine now.

---

### Post by davzd on 2015-06-05
Exactly what I was looking for. Thanks!

---

