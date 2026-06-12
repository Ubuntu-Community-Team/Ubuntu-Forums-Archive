---
title: "avast error fix for live cd"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-08-13
I need this for a live cd to run avast theses changed dont stick for a live cd

sudo gedit /etc/init.d/rcS

add
sysctl -w kernel.shmmax=128000000

or

edit in the /etc/sysctl.conf
add
kernel.shmmax = 67108864

---

### Post by jtarin on 2010-08-13
Are you trying to install WUBI?

---

### Post by linux18 on 2010-08-13
you want those changes to be applied to a live cd permanently?

---

### Post by lance bermudez on 2010-08-14
to fix the avast errror on a live cd run from the command line

sudo sysctl –w kernel.shmmax=128000000

then avast will run with out errors

---

