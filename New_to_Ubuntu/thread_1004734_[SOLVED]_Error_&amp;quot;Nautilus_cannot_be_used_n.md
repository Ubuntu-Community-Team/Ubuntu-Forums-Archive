---
title: "[SOLVED] Error: &amp;quot;Nautilus cannot be used now&amp;quot;.  Panel encountered fatal error."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by cheetaux on 2008-12-07
Hi,
Just today I started getting the following error windows after booting Ubuntu (8.10):

**Nautilus cannot be used now, due to an unexpected error.**  Nautilus cannot be used now, due to an expected error from Bonobo when attempting to register the file manager view server.

**The Panel has encountered a fatal error:** The panel could not register with the bonobo-activation server (error code: 3) and will exit.  It may be automatically restarted.

The GNOME does not start and I can not get into terminal.  Anybody know a fix for this or do I need to re-install.

Thanks

---

### Post by gettinoriginal on 2008-12-07
You can try this, 

[http://ph.ubuntuforums.com/showthread.php?t=755409](http://ph.ubuntuforums.com/showthread.php?t=755409)

if not, then google "ubuntu forums nautilus cannot be used now" and see if anything else may fix it

---

### Post by cheetaux on 2008-12-07
Yes, stupid me messed up my .bashrc or my .profile file.  I was able to boot into GNOME failsafe mode and correct the errors.  Thanks.

---

