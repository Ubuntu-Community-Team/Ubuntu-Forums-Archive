---
title: "Changing Network Driver - No modprobe.conf"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by vortexsurf on 2007-08-08
Hi, I am trying to get a 4 port nic working and need to change the auto detected driver, tulip to de4x5. I would usually use an alias in the modprobe.conf file but that file does not exist. I modified the aliases file with no luck.. when doing an lshw i still see "driver=tulip".

Any help would be greatly appriciated thanks!

---

### Post by Bosambo on 2007-08-08
You should enter the following into the terminal:

```
sudo gedit /etc/modprobe.d/blacklist
```

This will let you black list tulip and take de4x5 off the black list...

I hope

---

