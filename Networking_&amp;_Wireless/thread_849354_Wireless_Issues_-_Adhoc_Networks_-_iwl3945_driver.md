---
title: "Wireless Issues - Adhoc Networks - iwl3945 driver"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by crwstl on 2008-07-04
_Point #1_
Dear Ubuntu, I have an Acer Travelmate 8200 which uses the apprently pesky Intel Pro/Wireless 3945ABG for wireless internet.  How come in Gutsy it worked perfectly, and then you abandon me in Hardy making me spend countless hours googling fixes for this when I know nothing really about Linux!

_Point #2_
I finally got the iwl3945 driver to work by installing linux-backports and all that stuff, now my wireless will connect to networks and my LED is even lit back up.... but I cannot connect my wireless to an adhoc network for the life of me.  I routinely tether my Sprint Mogul wirelessly to my laptop for Internet.  It tethers just fine in Windows, but not in Ubuntu... after all my googling and searching and fixing, I cannot fix this.... Help!

---

### Post by JoeZ99 on 2008-09-04
Looks like network manager doesn't activate ad-hoc mode on the device.

check this out:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/201597](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/201597)

---

