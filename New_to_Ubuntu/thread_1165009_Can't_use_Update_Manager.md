---
title: "Can't use Update Manager"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by old_dope on 2009-05-20
I have been trying to install updates via the Update Manager but when i click on install i get the following message:

[CENTER]Unable to get exclusive lock[/CENTER]
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

Could someone tell me how to remedy this problem please. Thanks

---

### Post by snowpine on 2009-05-20
The error is pretty self-explanatory. Quit out of any other applications that can be used to add/remove/update/upgrade applications. If all else fails, reboot.

If that still doesn't work, try upgrading from the terminal (using the commands below) and post any errors here.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by old_dope on 2009-05-20
Have done as you suggested but was advised that i have 3 broken packages on my system and to use the "Broken" filter to locate them.

---

### Post by halitech on 2009-05-20
I think this should work
```
sudo apt-get -f install
```

---

### Post by DLG102282 on 2009-05-20
Uninstall the broken packages and try again.

---

### Post by _Purple_ on 2009-05-20
Try to run
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

