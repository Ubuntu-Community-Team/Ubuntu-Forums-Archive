---
title: "should i update the drivers of my graphic card?"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-25
on the site of ati i found a version of my graphic card which seems to be much more recent but im not sure if it really is
how can i check it ?
if it is, should i update it?

---

### Post by n-n-nebbl on 2011-02-25
which graphics card do you have?

if it is not too old, just use the fglrx drivers from the restricted drivers list

---

### Post by werty2010 on 2011-02-25
should i unistall the older one first?

---

### Post by werty2010 on 2011-02-25
i have the HD 5650 mobility radeon

---

### Post by n-n-nebbl on 2011-02-25
> **werty2010 said:**
> i unistall the older one first?

how did you install the older one?

usually you don't have to

---

### Post by werty2010 on 2011-02-25
through administration --> Additional Drivers

but the newer version is from the ati site in a *.run  file

---

### Post by n-n-nebbl on 2011-02-25
the version from additional drivers is tested and adjusted by ubuntu developers.

i recommend using the version you have.

if you want to use the newest one from ati (it may work too and better, but no guarantee) you cann simply execute the *.run file.

your ubuntu will only load one driver at once.
everytime you install one, it will be set to be loaded at boot time. (so you have to reboot after installation)

---

### Post by Paqman on 2011-02-25
Installing drivers manually gets to be a bit of a hassle. If the driver provided by Ubuntu is performing well enough I would just use that.

---

### Post by el_koraco on 2011-02-25
don't do it.

---

### Post by josephmills on 2011-02-25
If you have no lag on everything is fine. Then,if it not broken don't fix. Also the update manager (system>addmin>update manager)will help you if its not proprietary. If it is then the  additional drivers area will help you (system>addmin>additional drivers ) Not to say that you can't find better drivers sometimes but that is a rare situation.

---

