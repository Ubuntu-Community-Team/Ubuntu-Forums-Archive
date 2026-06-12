---
title: "Uninstall Linksys Driver"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by bmeyer on 2007-07-18
I need to uninstall the RT61 driver/module I installed several months ago.  I'm still getting familiar with Linux, so if anyone could walk me through it, I'd greatly appreciate it.

I'd like to fully remove everything RT61 related, not just blacklist it.  Thanks in advance for the help.

---

### Post by bmeyer on 2007-07-19
*bump*

I doubt this requires anything more than someone walking me through how to delete a linux kernel module.

---

### Post by roachk71 on 2007-07-19
You could simply uninstall ndiswrapper using synaptic or adept, but this approach would still leave the Windows NDIS driver on disk. If you would like to just remove the NDIS driver, use
```
ndiswrapper -l
```
to list the drivers installed, and use
```
ndiswrapper -e *drivername*
```
to remove the driver. (That's a lowercase 'L' in the first code snippet, by the way.)

---

### Post by bmeyer on 2007-07-21
Thanks -- the problem is that I didn't install it with ndiswrapper.  I need to delete the module from the kernel itself...

---

