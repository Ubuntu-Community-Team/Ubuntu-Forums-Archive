---
title: "uninstalling outside the repository"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by charlesdb on 2008-12-08
I installed the latest edition of clamAV from source forge, as the repository program is out of date. I'd like to uninstall it, because the signature update is failing, but I can't see any way of doing so.  Any help out there.  Thanks.
PS  Beginners lesson learnt. Use the repository.

---

### Post by binbash on 2008-12-08
If you installed the deb package, you have to find the exact name : 

sudo dpkg -l | grep clam 

When you find it, you can remove it via : 

sudo dpkg -r name

PS : you can also use -P instead of -r p = purge

---

### Post by geirha on 2008-12-08
... or use your favorite package manager, like Synaptic or aptitude. When you install deb-files they get registered in the same database as the packages installed from the repositories, so you can remove them in the same way as "regular" packages.

---

### Post by thelugnut on 2009-01-15
> .. or use your favorite package manager, like Synaptic or aptitude. When you install deb-files they get registered in the same database as the packages installed from the repositories, so you can remove them in the same way as "regular" packages.

I am afraid that is not correct.

I tried it and the program still runs.

binbash's answer works very well.

---

