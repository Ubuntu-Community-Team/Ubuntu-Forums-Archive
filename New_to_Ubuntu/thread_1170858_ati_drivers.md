---
title: "ati drivers"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Zom-b on 2009-05-26
how do I check what drivers I need for my ati card, I know what kind is it and was looking at the ATi website, but it has the ATi driver installer, then it has a driver set for Free86 and X.Org, I was just wondering how do I check to see if I need any of these or if I already have them?

---

### Post by Hendronicus on 2009-05-27
Have a look at System > Administration > Restricted Drivers Manager.

---

### Post by ugm6hr on 2009-05-27
Depends on what kind of ATI card.

ATI (AMD) has dropped support for older chipsets (see the AMD website for details), so you have to use the opensource ati (aka radeon) or radeonhd drivers (or vesa).  ati is the default opensource driver.

envyng will install the latest catalyst driver if you have a new supported card.

---

