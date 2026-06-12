---
title: "Restrict Access to Network at specified times"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by hatman on 2008-02-23
Is there a way to restrict users access to the network during specified times? For example between the hours of 00:00 and 07:00... I've looked and not been able to find anything... Never messed with the network side of things before....

---

### Post by Sam Lars on 2008-02-23
I'm sure that there's a way... it may be a "hack," but I'm sure it could be done.
For example, you could set up a firewall rule to block all outbound traffic, and cron it to apply that at 0000, and then restore the old rule at 0700...

---

