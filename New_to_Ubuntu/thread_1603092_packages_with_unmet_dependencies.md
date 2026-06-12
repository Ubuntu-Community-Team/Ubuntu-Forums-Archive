---
title: "packages with unmet dependencies"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by drascus on 2010-10-22
Using Ubuntu 10.10 with a Canon mp620 network printer:


Okay I installed cnijfilter packages and used these dpkg options:```
-i --force-architecture --ignore-depends=libcupsys2
``` I did this because without it my printer doesn't work. So now my printer works but the package manager keeps barking at me that I have packages with unmet dependencies and it won't update anything until I fix that issue. so initially I ran the fix but it just uninstalled cnijfilter so now I can't print. Does anyone know how I can get the package manager working and keep this package installed at the same time?

thanks.

---

### Post by drascus on 2010-10-22
Okay I fixed my own issue here. because the package worked even though synaptic said it was broken I just opened up gedit and edited: sudo gedit /var/lib/dkpg/status under the packages that said broken I deleted the dependecies from the depends line that weren't met. after that I stoped getting the error message.

---

