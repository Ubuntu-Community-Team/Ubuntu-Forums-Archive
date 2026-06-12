---
title: "Kernel Config"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by rwttaber on 2009-06-26
How do I view, not change, the kernel configuration? (Ubuntu 9.04)

---

### Post by KIAaze on 2009-06-26
```
less /boot/config-`uname -r`
```
or
```
less /boot/config-$(uname -r)
```

You can also reuse this config when recompiling your kernel as indicated in [https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

(You can of course also use more, cat, gedit, kate, vi, emacs, etc instead of "less")

---

### Post by sdennie on 2009-06-26
The above information is very good.  If you want to browse your kernel config in a more meaningful way, I suggest doing the following:

```

sudo apt-get install linux-source

```

You should then find a .tar.gz of your current kernel in /usr/src.  If you untar it and enter the directory it creates, the following will allow you to browse what you are a running in an interactive way:

```

make menuconfig
**or**
make gconfig

```

---

