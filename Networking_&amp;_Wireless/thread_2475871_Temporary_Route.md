---
title: "Temporary Route"
date: 2022-06-10
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-06-10
I've read up on routes within networks but can't quite get my head around them.

I have a vlan on my home network, one on the 192.168.2.0 network and another on 10.1.1.0

They are isolated but on occasions I would like access from one network to the other but not by default.  Now I know I can set ports on my router but that only works for incoming so I'd have to go out to internet and then back in again..

Is there a way to do this within my own LAN without going out then back again?

Geoff

---

### Post by MAFoElffen on 2022-06-11
I do this all the time for testing purposes. But... I do a lot of Virtual Hosts with Virtual Guest Machines, such as KVM.

I set up a VM that is a router setup to make temporary routes between my network segments. No cost in additional hardware. When I need that routed connection between, all I have to do it start that VM. Setup once, it's there for use when I need it.

You can do this many ways... But if you hard-wire it with config changes to existing hardware, then you would need to back off those changes, which would take time to back off those changes. (And risk downtime if you make a typo mistake) That's why I do it this way with a VM.

If you do decide to hardware config changes, I do backups of the router configs, then do scripts to change back and forth, between.

---

### Post by Geoff_Lane on 2022-06-13
> **MAFoElffen said:**
> I do this all the time for testing purposes. But... I do a lot of Virtual Hosts with Virtual Guest Machines, such as KVM.

I set up a VM that is a router setup to make temporary routes between my network segments. No cost in additional hardware. When I need that routed connection between, all I have to do it start that VM. Setup once, it's there for use when I need it.


My main machine is a 5 year old laptop so not able to run VM efficiently, as a result haven't tried that.

My router allows me to set up additional routes but I keep getting messages saying destination addresses cannot be same, think this is because even though the router is creating a vlan for me both subnets are on the same device.

Annoying because I can decline isolation of vlans (Can't see the point of that) or if I isolate, for the moment I cannot see a way round it.   Currently I just change WiFi as I run two SSIDs with one in each vlan.

Geoff

---

