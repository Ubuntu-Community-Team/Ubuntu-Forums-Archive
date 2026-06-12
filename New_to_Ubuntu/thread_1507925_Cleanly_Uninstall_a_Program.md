---
title: "Cleanly Uninstall a Program?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by GreenDance on 2010-06-12
I've been using sudo apt-get remove *program*, but i was wondering, does that fully uninstall a program or does it leave files behind?, i remember something about sudo purge program?

Thanks.

---

### Post by Bölvaður on 2010-06-12
> **GreenDance said:**
> I've been using sudo apt-get remove *program*, but i was wondering, does that fully uninstall a program or does it leave files behind?, i remember something about sudo purge program?

Thanks.

remove doesnt delete config files
purge removes config files.
purge is the same as completely uninstall in synaptic package manager

you dont need to use the command line if you dont want too btw, but you are much quicker using it if you know exactly what you are doing.


*added*
apt-get is the program. purge, remove, install and all that are just flags / arguments / parameters that apt-get takes in to know what you want to do.

---

### Post by K.Mandla on 2010-06-12
Moved to Absolute Beginner Talk.

---

