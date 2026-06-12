---
title: "Multiple NIC Problems"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by mrnoodle on 2005-05-09
I have a number of servers here running Hoary with multiple different brands of NIC cards.  The problem is the primary card comes active and works properly, but all of the additional cards fail to send traffic out the interface properly.  The IP addresses are staticly assigned and I can ping the local interface.  The route tables appear to be correct but any attempt to ping a device attached to the secondary interface fails.  The error message from the ping is "Hpost Unreachable"

Any ideas what could be causing this?

---

### Post by tonym on 2005-05-11
Have you added

ip_forward=yes

to /etc/network/options

?

---

