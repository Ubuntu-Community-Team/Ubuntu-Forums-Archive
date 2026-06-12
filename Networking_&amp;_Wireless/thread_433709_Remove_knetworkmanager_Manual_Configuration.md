---
title: "Remove knetworkmanager Manual Configuration"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by lowpis on 2007-05-05
Hi!

This is an idiot question, but I can't realize how to do this: I use Kubuntu Festy and I made a Manual Wireless Configuration in knetworkmanager. Now I want to remove this manual configuration but I don't see any option to do this!

How do I disable the manual configuration and use knetworkmanager normally?

Thanks!

---

### Post by NilsE on 2007-05-05
Go into the manual configuration and select the raoming option on each device in properties.

If that does not do it then also go into the   /etc/network/interfaces   file and just leave these 2 lines. (back it up first)

auto lo
iface lo inet loopback

---

### Post by lowpis on 2007-05-05
I didn't find that option in knetworkmanager. But editing that file manually and restarting the computer solved the problem.

Thanks!

---

### Post by apswartz on 2007-10-25
Thanks, this worked for me too. You should mark this thread as solved (in the thread tools) so others can easily find the solution.

---

### Post by KongKNoob on 2007-10-30
Or even better, make it Sticky. This solved things for me as well.

---

