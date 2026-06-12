---
title: "Change eth1 back to eth0?"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by valnar on 2006-10-20
I replaced a NIC in my Ubuntu Dapper PC and I had to start eth1 for it to come up.  Also, how do I change it back to eth0?  This is a regular P4 box with a PCI NIC.

/etc/network/interfaces has them both there.  How do I "un"-alias my current NIC from eth1 and put it back on eth0?

Robert

---

### Post by hanover.fiste on 2006-11-20
I have this same problem. I'd really like an answer, if anyone knows.

---

### Post by FrodoB on 2006-11-20
Your system is locking the MAC identifier of your old card to a certain identifier. To fix this you need to edit the /etc/iftab file and remove the reference of the old card to eth0. Edit the file using the following comand and remove the existing eth0 line:

$ sudo gedit /etc/iftab

That should do it.

---

### Post by hanover.fiste on 2007-01-19
Thanks! I'm still learning the debian/ubuntu way of doing things. I'm used to this stuff being done in ifcfg-ethX in the networking-scripts.

---

