---
title: "i need help with ubuntu software center."
date: 2010-12-21
forum: New to Ubuntu
---

### Post by mj360 on 2010-12-21
for some reason when i go to install or uninstall something in the ubuntu software center it say this

previous installation hasn't been completed
the installation could had failed because of an error in the  corresponding software package or it was cancelled in an unfriendly way. you have to repair this before you can install or remove any further software.

can anyone help me with this ?

---

### Post by Foxheadz on 2010-12-21
do you know the package name?

---

### Post by sffvba[e0rt on 2010-12-21
Strange error... in terminal you could try "sudo apt-get update" and also "sudo aptitude update"... may shed some more light on any issues...

404

---

### Post by Foxheadz on 2010-12-21
well first i would try doing sudo apt-get purge "name of app thats not working" and then reinstalling it

---

### Post by mj360 on 2010-12-22
i don't know, it doesn't say the package that needs to be remove

---

### Post by mj360 on 2010-12-22
i did sudo apt-get purge and everything works great again. thanks for all the help everyone. happy holidays everyone:D

---

### Post by sffvba[e0rt on 2010-12-22
> **mj360 said:**
> i don't know, it doesn't say the package that needs to be remove

> **mj360 said:**
> i did sudo apt-get purge and everything works great again. thanks for all the help everyone. happy holidays everyone:D

All is well that ends well I guess... glad you got it sorted... (I will remember the purge option in future if I have any hic-ups like this :))


404

Edit: You can mark this thread as solved, to help others see that your sorted ;)

---

### Post by Foxheadz on 2010-12-22
The purge command just completely delets all files from the package you select. So most problems caused by a faulty package should get fixed.

---

