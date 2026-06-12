---
title: "apt-get: how can I see what would be upgrade ?"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-11-08
I am learning command line and, curious as I am, I would like to know if there is a way to get a list of upgradeable packages after doing a apt-get update just before doing the apt-get upgrade :) 

Thanx

---

### Post by arpanaut on 2010-11-08
If you run sudo apt-get upgrade It will show you what is going to happen and ask you if you want to proceed. Hit y>enter if yes, n>enter if you wish to abort.

---

### Post by Mobidoy on 2010-11-08
> **arpanaut said:**
> If you run sudo apt-get upgrade It will show you what is going to happen and ask you if you want to proceed. Hit y>enter if yes, n>enter if you wish to abort.

Great thanks :)

---

### Post by papibe on 2010-11-17
What I do is use the "simulated" option of apt-get:
```
$ sudo apt-get -s upgrade
```
It shows me exactly "as if" is being upgraded (but it's not). Then I can backup conf files if necessary, and do the real update.
Regards.

---

