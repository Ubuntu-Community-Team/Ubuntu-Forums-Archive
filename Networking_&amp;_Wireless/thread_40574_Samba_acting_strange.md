---
title: "Samba acting strange"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by Seti on 2005-06-09
We have a desktop and a laptop, both with Ubuntu Hoary, and want to use samba to share files.
It was working so that my desktop (hostname:Phoebus) and the laptop (hostname:Juno) where both showing up under >Places>Network Servers in Nautilus along with "Windows network". If I go into windows network Phoebus and Juno both appeared there as well. 
Now I wanted to add another folder from my desktop to the two shares that were already mounted through >System>Administration>Shared folders, and added another folder to it. Now Phoebus no longer shows up at all. I made sure the properties for this new share were the same as those for the other two that were already being shared. I restarted samba with smbd restart, still nothing.
I rebooted and noticed a message that says "starting samba daemons...............failed."

Any ideas?

---

### Post by Seti on 2005-06-09
Somehow the issue has resolved itself.

(big sigh of relief)

---

### Post by crane on 2005-06-09
[QUOTE=Seti]Somehow the issue has resolved itself.

(big sigh of relief)[/QUOTE]

I love when that happens!!

---

