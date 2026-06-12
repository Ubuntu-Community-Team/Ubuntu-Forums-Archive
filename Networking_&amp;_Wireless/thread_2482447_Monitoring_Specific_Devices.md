---
title: "Monitoring Specific Devices"
date: 2022-12-31
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-12-31
Folks,

I have a fairly normal network setup, my router is my protector denying and incoming unless related to outgoing.  Router also has WiFi.

Is there a way my Ubuntu machine can monitor a specific device on my network?  In the past I have used wireshark and ntopng but unless other devices have a connection with my Ubuntu machine I don't appear to get any data.   My network interface is in promiscuous mode.

I know nmap can target a device, I am not expert but think nmap reports but doesn't monitor.

My router has some data on LAN statistics but is not very flexible and doesn't appear exportable.

If I want to monitor a specific device does it have to really go via my Ubuntu machine?

Any suggestions appreciated.

Geoff

---

### Post by TheFu on 2023-01-02
> If I want to monitor a specific device does it have to really go via my Ubuntu machine?

Uh, if you want Ubuntu to see the network traffic, then it needs to pass through the Ubuntu system.

A little understanding of the difference between hubs and switches might help.

In the olden days, we had "hubs".  Hubs were dumb and broadcasted every inbound packet through all outbound ports in the hub because it didn't know which specific port had the target package location MAC.  This could cause a "network flood" where effectively no packets would be able to get through. It was bad.

Then we got network switches.  These were a little smarter and they only send packets out the port where the target MAC is located. This requires the switch to keep track of which ports have which MACs connected.  A few kb of memory can hold hundreds of thousands of MACs.  We still got network floods, but that was due to the switch backplane limitations.  Cheap switches with fast ethernet (100 base-tx ports) might have a 200 Mbps backplane, so 2 systems talking full speed could overload the switch, if they pumped enough data for long enough.  They'd have to tell the sending machine to slow down, buffer is full.  That would also allow other systems to slide some of there packets into the switch and more systems/people were happier.  Best of all, systems that had no business seeing traffic not meant for them, never saw it.  It drastically improved network security.

So, it is next to impossible to buy a hub these days.  I have one from 1995, just for the ability to place a "tap" on the network near the router, but it drastically slows all the connectivity, because my normal switches  and routers are all GigE and that hub is only 10-base-tx.

People do make devices that can connect to higher end switches as dumb hubs.  They are almost novelty items now, but IT security people might help some.    High end switches have the ability to be configured to replicate all traffic out a specific "tap" port for network and security analysis.  These higher end switches aren't usually something a small business or home user would have.  There are some other terms for the same thing, like "port mirroring" or "port replication".

[https://forums.tomshardware.com/threads/looking-for-cheap-managed-switch-with-port-mirroring-monitoring.943762/](https://forums.tomshardware.com/threads/looking-for-cheap-managed-switch-with-port-mirroring-monitoring.943762/) has some cheap ideas using very old equipment that nobody should have on any internet connected network, but for a home lab, it wouldn't be terrible.  Just know that Cisco doesn't usually make patches available to anyone who bought equipment from unauthorized sellers.  They've killed the grey market doing this.  SAN equipment has the same problem, at least enterprise SAN equipment.  I've seen companies buy old storage frames to use as trade-ins to get what they really want 50% less from the competitor.  The used frame would never work, because they didn't have any licenses, but the new SAN vendor didn't know that.

Or get a better router, say opnsense, which has enterprise reporting and the ability to send SNMP to a different system for analysis.
[https://www.dnsstuff.com/network-monitoring](https://www.dnsstuff.com/network-monitoring) might be worth a read too.

---

### Post by Geoff_Lane on 2023-01-03
Thank you for a very informative reply.

Nowadays business has to satisfy the masses, most routers work reasonably well for most people.  I use sensible security measures, have a separate vlan for IOT devices and a wifi on a different subnet for if I want to keep some devices private.  Pretty sure not brilliant as wifi - whilst separate is on the same channel.

Guess really then the likes of wireshark and ntopng are really for servers.

My initial question was really aimed at trying to get details from an IP cam that only works off an android app.   Had this couple of years back, even the manufacturer help line said one could not access device from a PC so I sent them a screenshot of VLC on a laptop accessing the video.  The blink camera I have, scanned it with nmap using -p- (think that scans 65,000+ ports) and none open, UDP just shows port 68 filtered.  Only bought the device as it can be powered by USB so effectively portable, and it was on offer.   Useful security device I guess.

Geoff

---

