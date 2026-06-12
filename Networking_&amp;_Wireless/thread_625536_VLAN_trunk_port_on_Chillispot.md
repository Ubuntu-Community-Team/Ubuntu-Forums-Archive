---
title: "VLAN trunk port on Chillispot"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by jonallport on 2007-11-28
Hi Ubuntu people,

I don't know if this is possible but I'll ask anyway:

A friend has roped me in to help setup a hotel's networks, the back-office, sip, routing side is fine - bread and butter stuff! - OK

For the guest rooms there are 2 ethernet ports per room for guests to plug into for Internet access etc. - OK

I have setup a Chillispot portal to sit between the guests and the outside world to force acceptance of an AUP/terms and log activity. - OK

We want to screen the guests from each other, i.e. room 10 is isolated from room20 on the guest network in order that those intellectual executive types, who tend to leave open shares on their windoze machines accessible, can't lose their data to another guest.

The way I thought going about this was to put each room into its own VLAN and let the portal have visibility across all the VLANS.

This is a bit outside my comfort zone because:
(a) Chillispot uses the physical eth1 but creates a tunnel (tun0) to the guest network for routing
(b) Usually I would assign a subnet per VLAN, I need to just dish out the same DHCP address range across all VLANs (they will obviously have a common gateway)

vconfig doesn't seem to have an option for 'be a member of all VLANs' !!!

Any help gratefully recieved.

Many, many thanks in advance
Jon

---

### Post by jonallport on 2007-12-01
This is sorted now, thanks.

It turns out the 3com switches we're connecting to have an option of nominating a port to have visibility of all VLANs - this will do!

---

