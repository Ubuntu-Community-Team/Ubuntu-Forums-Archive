---
title: "CUPS eating my root partition"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2011-02-17
I came home today to find that my root partition was 100% full.  (previously I had around 7 gigs free)

After doing a little digging, I found out that my /var/spool/cups/tmp/ folder contains three files totaling 6.6gb.  I'm pretty sure they weren't there before.

They are named:
foomatic-wtSMag
gs_kYqOxZ
gs_mdpscC

Can I delete these files?  I assume so, because they're in a folder named /tmp, but I don't want to screw anything up.

I also am afraid to restart the computer until I have more space in my root partition.  Any advice would be appreciated.

---

### Post by stoogiebuncho on 2011-02-18
I got impatient and deleted them.  It put my root partition back at where it was before.

So far, no ill effects.  I restarted and everything seems to be working, including printing.

---

