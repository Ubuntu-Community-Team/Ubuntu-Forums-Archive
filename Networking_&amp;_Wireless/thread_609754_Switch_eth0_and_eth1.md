---
title: "Switch eth0 and eth1"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by DeepThoughts on 2007-11-11
I have a server running Ubuntu Server 7.10 which has two network adapters (one internal on the motherboard, one pci-card) and I need the current eth0 to become eth1 and the current erh1 to become eth0. As far as I know eth0 and eth1 are assigned according to which order they get loaded which means that I need to switch the order these modules are loaded in.

I've tried adding "blacklist forcedeth" and "blacklist 8139too" to /etc/modprobe.d/blacklist (hoping that I then could force the order with /etc/modules) but apparently that file doesn't works as I believed it did because the modules get loaded anyway.

So, how do you change the order these modules get loaded in? I've heard something about udev-rules but can't find any info on how I would create such a rule.

---

### Post by geforce123 on 2007-11-11
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

But tell me first, why do you need to swap eth0 and eth1 ?

---

### Post by DeepThoughts on 2007-11-11
The situation is this:

I've got a server with two network adapters. One will be facing the internet directly the other one will go to my router.

I've tried to just switch the cable but my ISP won't give me an IP then since they seem to have locked to it's MAC-address. Therefore my conclusion is that the simplest fix is to just switch eth0 and eth1

---

### Post by geforce123 on 2007-12-02
Ok but try this first: reset the cable modem with no computer plugged in, then plug the good cable, should now accept your "good" card.

---

