---
title: "Faulty battery level indication"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by sharan.kevryn on 2010-05-07
Ive installed the lucid lynx netbook remix on my acer aspire one 532h  netbook. The battery monitor seems to behaving funny. it doesnt seem to  be able to tell the correct "Energy when full". . .  here is what the power statistics show:

Energy: 40.7 Wh
Energy when full: 814.6 Wh
Energy( design) : 47.0 Wh
Percentage: 5.0 %

Can someone help me fix this. because the system hibernates even before the battery is actually drained . anyway i can set the Energy (design) to a default value?

---

### Post by Jon Monreal on 2010-05-07
It is likely [this bug]("https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/403303").

I would try making sure you have updated to the latest kernel (go to System>Administration>Update Manager, select "Check", let it check for new updates, and then select "Install Updates", restart, and see if this helps.

If this does not help, you could change the settings so your computer does not hibernate (it's not really running low on battery, and will continue to run until it actually runs out) or install an older version of UNR.

---

