---
title: "black listing"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Ryan Swanson on 2007-05-24
I'm following the guide posted for setting up my D-link wireless card, but I'm having trouble blacklisting the unneeded files.  I just don't know how to do it.  Can anyone tell me how, please?

---

### Post by ugm6hr on 2007-05-24
> **Ryan Swanson said:**
> I'm following the guide posted for setting up my D-link wireless card, but I'm having trouble blacklisting the unneeded files.  I just don't know how to do it.  Can anyone tell me how, please?

Not quite sure exactly what you're asking - but if you want to blacklist drivers / modules (e.g. if you want to ensure a certain wireless driver doesn't get used), then I think you just add a line as follows:

blacklist *driver*

to the bottom of /etc/modrope.d/blacklist (you may need to open as root to do this)

---

