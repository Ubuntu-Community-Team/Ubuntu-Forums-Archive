---
title: "Anyone using SR-IOV-capable networking equipment?"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by 1clue on 2014-01-20
Hi,

I've been planning a small network for awhile now, and suddenly realized that:
[LIST=1]
[*]My current network with 1gbe is slowed significantly by the ethernet cards.
[*]The cost of 10gbe is not really crazy anymore.
[*]10gbe is twice as fast as sata3
[/LIST]

The new network will contain:
[LIST=1]
[*]At least 2 (starting with 2) virtual machine hosts
[*]At least one NAS with good performance and 10gbe.  Maybe not enough to saturate the ethernet yet, but you gotta start somewhere.
[*]Several logical networks with firewalls between.
[*]A need to have each VM host contain multiple VMs which can be on different networks, and a need to make sure that security is enforced.
[*]A need to have the VLANs span the physical hosts, so there will necessarily be a lot of cross talk between the VM hosts.
[/LIST]

So I'm looking into network cards, came across single-root I/O virtualization as an extension of the vt-d idea.  I've read through the Intel docs [http://www.intel.com/content/www/us/en/pci-express/pci-sig-sr-iov-primer-sr-iov-technology-paper.html](http://www.intel.com/content/www/us/en/pci-express/pci-sig-sr-iov-primer-sr-iov-technology-paper.html) and understand it, and now I'm curious how many people might actually be using this technology?

The crazy thing is, these cards seem to be generally cheaper than the average 10gbe card.  And another thing that's crazy to me, when you follow the terminology and read up on it, and find real-world examples, it seems there are a lot of devices which have Linux support but nothing else.  No windows drivers, no mac, whatever.

This SR-IOV and its associated tech seems to be exactly what I need, but getting set up to use it would take a big bite out of the budget, and if it's not there yet then I'd rather wait a bit than buy a bunch of stuff that turns out to be useless or not up to its advertising.

Thanks.

---

