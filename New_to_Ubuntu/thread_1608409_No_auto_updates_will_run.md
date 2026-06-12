---
title: "No auto updates will run"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by phubert28 on 2010-10-29
My 64 bit Ubuntu 10.4 was a fresh install.

I UPGRADED to Ubuntu 10.10

Since then, Update Manager's "Install Updates" button (function) simply does NOTHING.

No messages, nothing.

In addition, though PlayOnLinux shows an update to 3.8.5 available, when I downloaded .deb package and double-clicked under FF downloads, it opens in Ubuntu Software Center, snows "Upgrade Available" (3.8.5) but when I select Upgrade "Upgrading..." shows but then returns to Upgrade Available without anything having been accomplished.

Finally, Update Manager is showing updates that are 'set aside' when I try to install manually!

These are the three that are failing:

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic


Any idea why I'm stuck???????

I seem to be getting farther behind day by day!!!

---

### Post by cariboo on 2010-10-31
There are probably some depends that need installing. Go to System->Administration->Synaptic Package Manager, and try updating there. Synaptic will tell you what packages need to be installed in order to complete and update.

---

### Post by phubert28 on 2010-10-31
Thanks! Never tried using Synaptic that way. I don't see any legend for highlighting, tho.

I clicked on "Mark All Upgrades" then looked for "linux" and one or two (or 3?) of the entries was highlighted in YELLOW.

Seems there are other packages in Linux that are similarly less than clearly documented.

---

