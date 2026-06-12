---
title: "Update Manager - No Longer Receive Updates"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-12
When I attempt tp launch Update Manager it simply clocks for ever...no longer receive updates...I am confortable with command line if I can fix the issue there.

Thanks

---

### Post by SuperSonic4 on 2008-12-12
```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

the first one checks for updates and the second installs them

---

### Post by drs305 on 2008-12-12
You may be able to figure out what is going on by looking at any error messages generated when you run the command from terminal. The Update Manager command is:
```

gksudo /usr/bin/update-manager

```

You can also try running these commands:
```

sudo apt-get update
sudo apt-get upgrade

```

You could also try to open synaptic or Software Sources and change your server in case that is the problem (Synaptic, Settings, Repositories, 'Download from').

---

### Post by gettinoriginal on 2008-12-12
sudo apt-get update   :p

---

### Post by Frank_F on 2008-12-12
when i attempt to use gksudo /usr/bin/update-manager I receive warning could not initiate bus...when I use

sudo apt-get update
sudo apt-get upgrade

I receive no updates...which is impossible as I havent receive any in months

---

### Post by colintivy on 2008-12-12
Any chance that your internet connection is bust ?

colintivy :-\

---

### Post by Frank_F on 2008-12-12
using right now...appears fine

---

### Post by drs305 on 2008-12-12
> **Frank_F said:**
> when i attempt to use gksudo /usr/bin/update-manager I receive warning could not initiate bus...

Could you post the exact error message you get?  

Also, are you able to open synaptic and change repositories? (Probably not the problem but you never know...)

---

### Post by Frank_F on 2008-12-12
Error Message I receive...thanks

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by philinux on 2008-12-12
Post the output of this.

cat /etc/apt/sources.list

Wrap it with code (#)

---

### Post by Frank_F on 2008-12-13
That seems to have worked...thanks

---

### Post by Frank_F on 2008-12-15
updated to 7.10 and still cant use update manager...i receive "Failed to run /tmp/tmpFmW-Wa/hardy as user root"

---

