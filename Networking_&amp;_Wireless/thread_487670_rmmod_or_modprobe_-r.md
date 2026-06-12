---
title: "rmmod or modprobe -r"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2007-06-29
If we use one of those commands to remove a module, will that module come back when the computer reboots?

I was thinking that it only removes it during this boot cycle and it will return upon reboot.  If we wanted it to be permanently gone, we would just blacklist it.  Is that correct?

Edit:
I was not fast enough so my comment is now repetitively redundant...

---

### Post by into_311 on 2007-06-29
that is correct. rrmod or modprobe -r only temporarily unloads the module. If you were to reboot, it will come back in be default.

To prevent the module from loading you will want to blacklist it.  this should be found in /etc/default/linux-restricted-modules-common file.

```
 vim /etc/default/linux-restricted-modules-common 
```

add the module you wish to blacklist in there. Edit disabled_modules to include the module you with to blacklist.

---

### Post by Rui Pais on 2007-06-29
> **into_311 said:**
> that is correct. rrmod or modprobe -r only temporarily unloads the module. If you were to reboot, it will come back in be default.

To prevent the module from loading you will want to blacklist it.  this should be found in /etc/default/linux-restricted-modules-common file.

```
 vim /etc/default/linux-restricted-modules-common 
```

add the module you wish to blacklist in there. Edit disabled_modules to include the module you with to blacklist.

Aren't that list just for modules inside linux-restricted-modules? 
The general blacklist for modules is at:
/etc/modprobe.d/blacklist (or /etc/modprobe.d/blacklist-*)

---

### Post by Ayuthia on 2007-06-29
Now, what is the difference of blacklisting modules in /etc/modprobe.d/blacklist and /etc/default/linux-restricted-modules-common?

---

### Post by Rui Pais on 2007-06-29
> **Ayuthia said:**
> Now, what is the difference of blacklisting modules in /etc/modprobe.d/blacklist and /etc/default/linux-restricted-modules-common?

cat /etc/default/linux-restricted-modules-common
> # This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.


hth

---

