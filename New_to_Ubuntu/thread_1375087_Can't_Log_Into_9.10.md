---
title: "Can't Log Into 9.10"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by bearglenn on 2010-01-07
I have a virtual machine running 9.10.  

We had a power outage, and our ESXi server had issues restarting those have been resolved.  

All of my VMs are working expect, the Ubuntu 9.10 machine.  When I turn tit on it gets to the logon screen, where I receive this error message:
      Install problem!
      The configuration defaults for GNOME
      Power Manager have not been installed Correctly,
      Please contact your computer 
      administrator

If I try to log in, the machine just reboots.  I do have telnet access.

Any Ideas?

---

### Post by Buuntu on 2010-01-07
Boot into recovery mode (should be an option in the grub menu).  From the options that come up, choose to drop down to a root shell.  From there try running these commands.
```
apt-get update
apt-get upgrade
apt-get install -f
apt-get dpkg --configure -a
```
Restart the VM and see if it boots normally.

---

