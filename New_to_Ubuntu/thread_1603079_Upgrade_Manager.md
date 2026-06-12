---
title: "Upgrade Manager"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by mikemykel on 2010-10-22
I upgraded from 10.4 to 10.10 and all is well except that now the Upgrade Manager, although it appears, will not respond to the install button. I have a lot of upgrades backed up and am getting nervous.

---

### Post by Hippytaff on 2010-10-22
you can always type
 
```

sudo apt-get update && sudo apt-get upgrade

```
into the terminal, until you fix the update manager :-) (open terminal with CTRL+ALT+T)

---

### Post by silbak04 on 2010-10-22
Open up a terminal, and type in:

```

$ sudo apt-get update && sudo apt-get upgrade

```

*Looks like someone beat me to it*

---

### Post by migs73 on 2010-10-22
I had this problem for a bit, try running update manager manually (System > Administration > Update Manager) and then press the install button. That worked for me, then one of the updates must have sorted the problem.

---

### Post by Hippytaff on 2010-10-22
> **silbak04 said:**
> Open up a terminal, and type in:
 
```

$ sudo apt-get update && sudo apt-get upgrade

```
 
*Looks like someone beat me to it*
 
only just :-D

---

