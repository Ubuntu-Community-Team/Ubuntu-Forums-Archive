---
title: "How to install a Driver as a root?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by GeneralShep on 2011-07-16
Hey I'm trying to install my Nvidia GeFore 9800 GT Video Card drivers. But When ever I run it it says "Nvidia Installer must be run as root" It is a .run file. Can anyone tell me how to do this?

---

### Post by gandaran on 2011-07-16
use 'sudo' at the beginning of the install command, sudo allows the user temporally root rights, there's no need to use any other method in ubuntu.
```
sudo ./file to install.run
```

---

### Post by CatKiller on 2011-07-16
Is there a reason you aren't using the version in the repositories? Downloading random stuff off the Internet and trying to run it isn't generally the best way of doing things with Ubuntu.

---

### Post by Bucky Ball on 2011-07-16
> **CatKiller said:**
> Is there a reason you aren't using the version in the repositories? Downloading random stuff off the Internet and trying to run it isn't generally the best way of doing things with Ubuntu.

+1. Always check the repos first. System>Administration>Synaptic Package Manager.

---

### Post by Bucky Ball on 2011-07-16
Ah, GeneralShep. Hang on. Go here:

System>administration>hardware drivers. switch it on.

If you have no Nvidia driver there, do an update and restart and look again. ;)

---

