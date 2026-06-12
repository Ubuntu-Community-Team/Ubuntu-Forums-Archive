---
title: "how to upgrade from 10.10RC to 10.10 ?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by the.phantom on 2010-10-10
is it possible to just upgrade from the RC to 10.10
i have software sources set to check for normal upgrades
 i have the rc set up nice and would like a easy way and not a fresh install if possible

thanks

---

### Post by andrewthomas on 2010-10-10
You don't have to do anything but

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by PaulW2U on 2010-10-10
If you're happy that everything is working as it should then just check for updates. Once fully updated you will have the final release.

To check type **lsb_release -a** in a terminal. If there is no mention of 'development version' then you will have the final release.

---

### Post by the.phantom on 2010-10-10
thanks for the quick replies !!!!!
no mention of development  and no updates so one happy guy here ;-D

---

### Post by kroq-gar78 on 2010-10-10
"That was easy!"

---

### Post by bioShark on 2010-10-10
```
lsb_release -a
```

gives me this output:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
```


Does this mean the upgrade has already been performed? And I am using a clean 10.10?

Thanks

---

### Post by maciej234 on 2010-10-10
> **rollandsov said:**
> ```
lsb_release -a
```gives me this output:

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
```
Does this mean the upgrade has already been performed? And I am using a clean 10.10?

Thanks


Yes! enjoy

---

### Post by bioShark on 2010-10-10
Thanks

---

### Post by andrewthomas on 2010-10-10
> **PaulW2U said:**
> If you're happy that everything is working as it should then just check for updates. Once fully updated you will have the final release.
 
To check type **lsb_release -a** in a terminal. If there is no mention of 'development version' then you will have the final release.
 
that info was changed maybe six days ago, not a relavent indication

---

### Post by bioShark on 2010-10-11
So then what is a definite method to check that I am on 10.10 and not the RC?

---

