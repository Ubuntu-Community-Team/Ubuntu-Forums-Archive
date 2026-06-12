---
title: "Commnad Line Only Package list"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by dwaine256 on 2010-05-29
I know this is going to sound strange but does anyone have or know where to get a list of the packages that are installed when a 10.04 LTS Command Line Only installation is done on any variant?  

I could take the time to go and wipe my laptop and then reinstall lubuntu 10.04 and get it myself but would prefer to find an online resource.

Thanks

---

### Post by nothingspecial on 2010-05-29
```
apt-cache showpkg ubuntu-minimal
```

---

### Post by sisco311 on 2010-05-29
The kernel (linux-image), ubuntu-minimal, ubuntu-standard and their dependencies.

---

### Post by gmargo on 2010-05-29
> **dwaine256 said:**
> 
I could take the time to go and wipe my laptop and then reinstall lubuntu 10.04

Don't destroy your working setup.  This is the perfect use for a Virtual Machine.  Create a new VM and install on that.  (I have one Hardy system but 20 or so virtual machines of other releases and distributions; all just for testing purposes.)

---

