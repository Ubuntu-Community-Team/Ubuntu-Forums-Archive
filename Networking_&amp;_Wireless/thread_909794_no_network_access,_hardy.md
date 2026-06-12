---
title: "no network access, hardy"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by v4g480nd on 2008-09-03
Recently my network stopped working and my router can see the computer, mac and computer name.  I've tried switching NICs and each NIC gets a new address, all visible from the router but nothing can be accessed from said computer.  I popped in the hardy live disk and everything worked.  So how can i make my install work like the live cd?

---

### Post by Iowan on 2008-09-04
Check (or post) results of **ifconfig** and contents of **/etc/network/interfaces** file.  Verify an "auto" line exists for NIC.  It's possible that router has problems with IPv6, (which can be disabled).

---

