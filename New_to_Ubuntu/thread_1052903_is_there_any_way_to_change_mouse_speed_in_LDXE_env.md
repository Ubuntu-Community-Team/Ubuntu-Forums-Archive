---
title: "is there any way to change mouse speed in LDXE environment"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by imlinux on 2009-01-28
i have installed lxde environment, but finds mouse cursor to be little slow i want to change it according to my requirement, but can't find any settings to do so, any help will be highly appreciable.

---

### Post by swoody on 2009-02-17
Try out different values in a console with xset m.
For example:
```
xset m 3 2
```
(The first number is the speed and the second is the threshold)
Then put in the values you like most into .xinitrc

If that doesn't work, try editing the 'Sensitivity' in xorg.conf

Let me know if either of those work or not :)

---

