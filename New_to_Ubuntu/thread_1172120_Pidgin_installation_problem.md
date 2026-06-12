---
title: "Pidgin installation problem"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-05-28
I'm getting this error when trying to install Pidgin from Synaptics:

Please insert the disk labeled:
Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)
in drive /cdrom/

I'm using Ubuntu 9.04. Anyone know how to get around this?

Thanks.

---

### Post by _Purple_ on 2009-05-28
Go to System> Administration> Software sources and if you have CD listed there, remove the tick beside it. Then type in terminal
```
sudo apt-get update
sudo apt-get install pidgin
```

---

### Post by h8uthemost on 2009-05-28
Ha! That worked. Thank you so much _Purple_.

---

### Post by _Purple_ on 2009-05-28
You are welcome. :)

---

