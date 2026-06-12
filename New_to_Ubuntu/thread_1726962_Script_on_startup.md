---
title: "Script on startup"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by Drezard on 2011-04-11
Is there any easy way to execute a script on startup for a system I don't have root access to.

Need to run a network management application to manage some routers I have on a network but don't have full root access to the box. 

This script needs to be run on startup thats about it. No root access to box. Only one user access.

---

### Post by LostFarmer on 2011-04-11
try System/Preference/Startup Aplications-add and fill path/name in the box.  I do not know at what startup stage it is ran.

---

### Post by Cheesehead on 2011-04-11
If the system has cron, you can create an @reboot job in your crontab.

---

