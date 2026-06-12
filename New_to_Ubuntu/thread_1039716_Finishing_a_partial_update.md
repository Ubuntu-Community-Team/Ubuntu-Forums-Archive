---
title: "Finishing a partial update"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by sbussy89 on 2009-01-14
Ubuntu tried to install an update to virtualbox while I was running virtualbox.  It gave me an error because VB's kernel was running, and did not install the update.  The problem is, ubuntu no longer recognizes that I need this update, and I think I *really* need it because I cannot get internet connection inside of the virtual box.  Is there any way to force ubuntu to realize that I still need this update?

---

### Post by jemate18 on 2009-01-14
> **sbussy89 said:**
> Ubuntu tried to install an update to virtualbox while I was running virtualbox.  It gave me an error because VB's kernel was running, and did not install the update.  The problem is, ubuntu no longer recognizes that I need this update, and I think I *really* need it because I cannot get internet connection inside of the virtual box.  Is there any way to force ubuntu to realize that I still need this update?

what process did you used for the update?

---

### Post by sbussy89 on 2009-01-14
Update Manager

---

### Post by king EZi on 2009-01-14
Try

$ sudo apt-get update <package name>

---

### Post by jemate18 on 2009-01-14
> **sbussy89 said:**
> Update Manager

If you go to 
System -> Administration -> Update Manager

Do you still see the entry there?

---

### Post by sbussy89 on 2009-01-14
no that's the problem, it seems to think it installed  already but im pretty sure it quit prematurely

---

### Post by handydan918 on 2009-01-14
> **sbussy89 said:**
> no that's the problem, it seems to think it installed  already but im pretty sure it quit prematurely
Why?

---

### Post by sbussy89 on 2009-01-15
mid-install, in said something about the virtualbox kernel running, and then just stopped... i did fix the internet problem though, had to change the adapter, so as of right now this may not be a problem after all... thank you for the help :)

---

