---
title: "How does network-manager interact with the old network configurations?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by daviddehoog on 2007-12-03
Hi all

I've been exploring the variety of network configuration options available in Gutsy and I'm now somewhat confused. I've searched around, read the GNOME live and project pages, and I'm struggling to grasp how network-manager interacts with the old network configurations ... Is there a resource that I've missed which explains the interaction ?

As I understand it, network-manager will only try and manage (with avahi and dbus as intermediaries) devices not specified in the old /etc/network/interfaces file. Network-manager also makes use of the if-(up|down)-style scripts to link tasks to changes in network interface.

I've got a Thinkpad T42 with both wired and wireless interfaces, and I use it in about 5 different configurations.
- Home 1 (wireless)
- Uni (wireless)
- Uni (wired)
- Home 2 (wireless)
- Separate network (wired - Static IP, as DHCP server, webserver, etc.)

If I configure the three wireless connections with network-manager, and then have multiple wired connections specified in the old /etc/network/interfaces scripts ... How will the OS know which configuration to use ? What happens if a wired cable is plugged in - network-manager apparently gives priority to wired connections - but I'm not asking it to manage them ? What about the old ifplugd ?

I'm a bit confused about how all of these pieces of a very complicated puzzle will work peacefully together ... Am I missing something ?

Cheers
Dave

---

