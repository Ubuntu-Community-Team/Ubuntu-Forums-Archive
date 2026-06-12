---
title: "Unable to install things..."
date: 2011-04-19
forum: New to Ubuntu
---

### Post by ESDEEM on 2011-04-19
Following appears ehrn use apt-get commands....
> esdeem@esdeem:~$ sudo apt-get install libasound2-plugins
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
pls help me to fix this....

---

### Post by Thijk on 2011-04-19
Did you close the synaptic package manager?

---

### Post by arochester on 2011-04-19
You can only use ONE package manager at a time, whether apt, aptitude, synaptic, kpackage etc. They all use just one database so only one can access it at a time. Close all open applications, open ONE and try again.

---

### Post by seawolf167 on 2011-04-19
As the other posts said, ensure you only have one package manager open. This includes other terminals that are installing/updating/upgrading your system.

i.e. If you open a terminal and run

```
sudo apt-get update && sudo apt-get upgrade
```

you *cannot* open another terminal and run

```
sudo apt-get install *programname*
```

until the 1st terminal finishes and releases the directories/files

---

