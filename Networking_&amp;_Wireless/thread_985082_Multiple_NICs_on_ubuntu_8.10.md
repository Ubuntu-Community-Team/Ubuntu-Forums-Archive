---
title: "Multiple NICs on ubuntu 8.10"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by ramon82 on 2008-11-17
Hi all,

I just installed Ubuntu 8.10 on a PC having 4 NICs. The integrated one is working OK but when I connect the UTP to the rest (which are all PCI) there is no activity as if they were disabled or not working. I confirmed that they all work as before it had XP installed and I could work with all.

How can I get the rest of the NICs to work? is there a way how I can enable them?

Thanks!

---

### Post by Iowan on 2008-11-17
Start with **ifconfig -a** to see if they got addresses.  If not, you can check /etc/network/interfaces to see how they're set up.  I suspect you'll need to set static addresses, which (unless an update has fixed it) is a problem with Network Manager.  A potential workaround is [here]("http://ubuntuforums.org/showthread.php?t=974382").

---

