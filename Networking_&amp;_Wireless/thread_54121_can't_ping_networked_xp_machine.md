---
title: "can't ping networked xp machine"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by linuxNewb on 2005-08-03
I know that XP machines require non-XP machines to run that "network setup" disk in order to work with them, but how can I do this with my Ubuntu box? I feel like I should at least be able to ping the XP box.

I never ran that disk on my Windows 2000 box, and it can't ping the XP box either. I am able to share files with the 2000 box without issue.

The kicker is that the XP box can access the 2000 box and share files without a problem even though the 2000 box can't even ping it. What's that about?

Any help here would be much appreciated. Thanks in advance.

NOTE: I know that this may not be Ubuntu specific, so please remove this thread if it doesn't belong here.

---

### Post by grim42 on 2005-08-03
Your problem is almost certainly caused by XP's firewall blocking ICMP traffic.

This shouldn't affect your ability to access the XP system's shares via Nautilus with smb://<xpname>/<sharename> or via Places/Network Servers/etc.

---

### Post by linuxNewb on 2005-08-04
That was it, thank you so much  :)

---

