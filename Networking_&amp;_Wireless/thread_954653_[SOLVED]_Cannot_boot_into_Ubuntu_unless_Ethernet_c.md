---
title: "[SOLVED] Cannot boot into Ubuntu unless Ethernet cable is attached"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by GenePayne on 2008-10-21
I'm running Ubuntu 8.04 on a lenovo T61 ThinkPad laptop. When I boot up at work with an Ethernet cable attached, everything is fine. However, when I boot up at home without the cable, I can't get past the login--it just stays indefinitely at the blank brown screen.

I am able to get into Ubuntu if I select the GNOME failsafe session, but then some programs do not run correctly (I assume since certain startup scripts are not run in failsafe mode) so this would not be a good long-term solution.

Any ideas on how to fix this?

---

### Post by GenePayne on 2008-10-22
(Follow-up to marking this thread solved)
From /var/log/messages, discovered that my /etc/fstab was trying to mount a network file system, and without the Ethernet cable it couldn't accomplish this and so it hung. Switched this to auto-mount and solved the problem.

---

