---
title: "Problems with visuals"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by itsvan on 2008-12-25
Hey everyone,,i have problmes with my special effects and all that stuff on ubunut,,they wont activate for some reason,,maybe something gout messed with,,how can i fix it???

---

### Post by Temposs on 2008-12-25
Go to System->Administration->Hardware Drivers and make sure your recommended graphics driver is activated. If it's not, then activate it :-)

---

### Post by itsvan on 2008-12-25
the box is empty and says no proprietary drivers on system...??? what does that mean??

---

### Post by nhasian on 2008-12-25
if the hardware drivers list is empty ubuntu didnt detect any compatible propriety drivers.  lets see what video card you have.  in a terminal type:

```
lshw -C display
```

---

