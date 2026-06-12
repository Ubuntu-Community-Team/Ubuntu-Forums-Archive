---
title: "nameif  /etc/init.d/networking suggestion"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by gberanek on 2006-10-12
Occasionally after an update on a machine with multiple NIC's the names of network interfaces may switch.  e.g. eth0 becomes eth1 and eth1 becomes eth0.  This is due to the fact that they are named in sequence as they are found, and an update can change that order.  To avoid this we use nameif.  But, as man NAMEIF(8) clearly states, "nameif  should be run before the interface is up, otherwise it’ll fail."  So I have the following suggestions:

1.) /etc/init.d/networking should check for the existence of a non-zero length /etc/mactab file and if it exists it should execute nameif.

2.) install should create /etc/mactab, at least on server installs.

---

### Post by brokenthorn on 2006-10-13
Yes, I think it is because of the fact that UDEV loads the modules for the specific NICs in parallel and it does not load them in the same order every time. One other solution is to create udev-rules to rename the interface based on their Hardware Address or PCI ID. This is what I've been using on Gentoo, ArchLinux or Slackware. I have a fresh install of Xubuntu and I will leave the machine on and wait for more input on this issue before I go with my usual if nothing "better" comes up.

---

