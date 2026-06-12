---
title: "cant install a package"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by basilwatson on 2010-05-17
Hi all 
I am having a great deal of problems installing a package 
i keep getting this warning 

(Reading database ... (Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%(Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 339726 files and directories currently installed.)
Unpacking togl (from .../togl_1.7-0ubuntu4_amd64.deb) ...
dpkg: error processing /home/caelinux/Desktop/togl_1.7-0ubuntu4_amd64.deb (--install):
 trying to overwrite '/usr/lib/libTogl1.7.so', which is also in package libtogl 0:1.7-1
Errors were encountered while processing:
 /home/caelinux/Desktop/togl_1.7-0ubuntu4_amd64.deb


I have Just upgraded from 8.04 to 10.04 everything went well but ,,,I cannot install a critical program I need 

netgen 

as I keep getting the above message 

I have tried manually to remove but it will not install !

Any Ideas ?

Stephen

---

### Post by drs305 on 2010-05-17
> **basilwatson said:**
> 
Unpacking togl (from .../togl_1.7-0ubuntu4_amd64.deb) ...
dpkg: error processing /home/caelinux/Desktop/togl_1.7-0ubuntu4_amd64.deb (--install):
 trying to overwrite '/usr/lib/**libTogl1.7.so**', which is also in package libtogl **0:1.7-1**
Errors were encountered while processing:
 /home/caelinux/Desktop/**togl_1.7-0**ubuntu4_amd64.deb

Any Ideas ?


It looks like a dependency problem. Offhand, it appears you are trying to install a 1.7-0 deb file but already have the 1.7-1 dependencies installed.

Can you obtain a later version of the deb file you downloaded?

---

### Post by basilwatson on 2010-05-17
> **drs305 said:**
> It looks like a dependency problem. Offhand, it appears you are trying to install a 1.7-0 deb file but already have the 1.7-1 dependencies installed.

Can you obtain a later version of the deb file you downloaded?

no I cant find one , sort of lost at the moment 

Stephen

---

