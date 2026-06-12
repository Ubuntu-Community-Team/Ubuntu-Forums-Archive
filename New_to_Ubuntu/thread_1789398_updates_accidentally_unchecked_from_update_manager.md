---
title: "updates accidentally unchecked from update manager"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by lamigam on 2011-06-23
hi
I have ubuntu 11.04.
I accidentally unchecked some updates from update manager that were already downloaded but not installed.
I installed the rest that were installed.
now I want to install those updates I unchecked for installation but the update manager says "There are no updates to install"

---

### Post by wildmanne39 on 2011-06-23
> **lamigam said:**
> hi
I have ubuntu 11.04.
I accidentally unchecked some updates from update manager that were already downloaded but not installed.
I installed the rest that were installed.
now I want to install those updates I unchecked for installation but the update manager says "There are no updates to install"
Hi, run this command from a termainal and see if yo can install them that way.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by lamigam on 2011-06-23
> **wildmanne39 said:**
> Hi, run this command from a termainal and see if yo can install them that way.
```
sudo apt-get update && sudo apt-get upgrade
```

result:
> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


no error messages

---

### Post by wildmanne39 on 2011-06-23
> **lamigam said:**
> result:

Hi, you do not have any update at this time or that command would have installed them, are you sure that in another update you did not install them?

---

### Post by lamigam on 2011-06-23
> **wildmanne39 said:**
> Hi, you do not have any update at this time or that command would have installed them, are you sure that in another update you did not install them?

I clicked "Check" in the update manager. ("these updates were downloaded but not yet installed" it said)
I unchecked most of them and clicked "Install Updates"
the next time I clicked "Check" - the unchecked updates were gone from the list of updates. not installed. gone from the list.
they were security updates so I'm worried.

---

### Post by wildmanne39 on 2011-06-23
> **lamigam said:**
> I clicked "Check" in the update manager. ("these updates were downloaded but not yet installed" it said)
I unchecked most of them and clicked "Install Updates"
the next time I clicked "Check" - the unchecked updates were gone from the list of updates. not installed. gone from the list.
they were security updates so I'm worried.The next time you ran the update manager it would have installed them, maybe you just did not notice, that command you ran would have installed them if they are not installed already.

---

