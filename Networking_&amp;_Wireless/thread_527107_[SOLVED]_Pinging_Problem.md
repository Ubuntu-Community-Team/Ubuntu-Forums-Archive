---
title: "[SOLVED] Pinging Problem"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Irony on 2007-08-16
I have a wired connection to a bthomehub.;

[PHP]00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)[/PHP]

It is however erratic when it comes to pinging it. It will start off fast;

[PHP]64 bytes from BThomehub.home (192.168.1.254): icmp_seq=3 ttl=64 time=4.85 ms[/PHP]

but drop off to;

[PHP]64 bytes from BThomehub.home (192.168.1.254): icmp_seq=3 ttl=64 time=236 ms[/PHP]

or completely stop with 100% packet loss - it may take an hour or two for this to happen. It does this in ubuntu or windows and thus makes browsing impossible. I can reboot into ubuntu or windows but the problem will still be there.

Yet if I connect my laptop through the same ehternet cabling its fine.

I assume therefore that my LAN port is faulty on my Asus A8V Deluxe motherboard. I don't know why it usually starts off okay when I first boot up - perhaps a heat related warming up of the circuits involved?

To test this could I use one of my PCI slots to insert a new LAN card or alternatively use a USB to LAN connector -  would I have to do some configuring for these alternatives or does Ubuntu automatically detect them on start-up?

Any help in solving/determing the problem would be appreciated.

---

### Post by lloyd_b on 2007-08-16
You mention that after a while the network link goes completely dead (100% packet loss).  Question: If you do a reboot at that point, does the link come back up, and how fast or slow is it after the reboot?

If a reboot brings it back to "normal", then you may be looking at device driver issue (though I've never heard of a driver problem with those particular symptoms).

If after a reboot the link is still very slow/dead, then I'd suspect that it is a hardware issue - your description of the problem is consistent with a temperature-related fault, where the hardware works well when cold, but starts to fail when it warms up.

(There's a techie trick for confirming this type of issue, but it requires identifying the chips involved, letting them warm up, then hitting them with a blast of compressed air to cool them rapidly.  You can try this if you know your way around a motherboard...) 

As for using a different ethernet device: most PCI Ethernet cards will recognized automatically.  USB devices should also be automatically recognized, provided that there is a driver for them (you're less likely to hit a no-driver situation with a PCI card than with a USB device, but this is an issue that can affect you with either).  I'd recommend picking up a commodity 10/100 Ethernet card (3Com cards are well supported) unless you need gigabit speed.

Be advised - the new device (be it PCI or USB) will appear as "eth1", since "eth0" is claimed by the on-board device.  But if you connect to the new device, and leave the old device unattached, Ubuntu should auto-configure everything for you (assuming you're getting your configuration from a router via DHCP).

Lloyd B.

---

### Post by Irony on 2007-08-17
Thanks for the advice lloyd_b  -  much appreciated.

I'll maybe try the PCI approach and report back.

---

### Post by Irony on 2007-08-20
I seem to have located the problem.

It is the bthomehub - it is in some way incompatible with my desktop though fine with the laptop.

I know this because I reconnected my old voyager 2100 and everything works fine.

Problem is the bthomehub is needed for the internet phone.

At least it seems my desktop is okay.

---

### Post by Irony on 2007-09-03
Okay I've discovered the real problem... signal strength.

The problem also started on the voyager 2100, so eventually I put back the bthomehub.

However I put the bthomehub right next to my computer so that the cable is only about 2 metres long - it was formally wire connected via a home plug system.

Whereas it used to ping at 4 ms on a good day it now pings at 0.7 ms - this has dramatically increased download and browsing speeds.

However this means the laptop is now located a long way from the hub - but by a lot of trial and error positioning of the hub I seemed to have got a good enough signal strength to the laptop so it hasn't suffered yet.

---

