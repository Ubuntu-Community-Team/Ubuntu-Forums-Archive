---
title: "Swapping NICs"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Nfzgrld on 2008-08-14
My 8.04 server has two integrated LAN adapters, An Intel 82557 10/100 and an Intel 82540EM Gigabit adapter. I'm currently using the 82557 exclusively but am having some problems with it. I'd like to switch to the other adapter, but I'm not sure what the best way is to go about doing that. They both show up under lspci and are both listed when I do lshw -C network. What's the best procedure to do this?

---

### Post by Iowan on 2008-08-14
You might be able to disable one or the other in the BIOS for a semi-permanent solution.  Otherwise, check **/etc/network/interfaces** file to see which (if either) has an "auto" line.  If the one you currently use has one and the other does not, you might be able to switch simply by changing that line.

---

### Post by Nfzgrld on 2008-08-14
I tried turning the first one off in the bios and the other on but that didn't seem to do anything. It acted like there was no ethernet until I switched it back. In looking at the interfaces file I find there is an auto setting for eth0, but not for eth1. Should I change that line to reflect eth1 and just leave eth0 out in the "ether?"

---

### Post by Iowan on 2008-08-14
That'd be the easy way - and easy to put back if it doesn't work - or if you want to go back the other way.

---

