---
title: "Cairo-Dock Uninstall Problem"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Haris-MV on 2009-12-07
I have removed Cairo-Dock using Commands but still this one appears and it does start when I click

[IMG]http://img31.imageshack.us/img31/9217/screenshotug.png[/IMG]

---

### Post by ajgreeny on 2009-12-07
Reboot?  The program may still be running in memory if you have not rebooted, or at least logged out and in again.

---

### Post by Haris-MV on 2009-12-08
I rebooted It's still there

I tried to remove it again. but its not working

> 
haris@ubuntu:~$ sudo apt-get remove cairo-dock cairo-dock-plug-ins
[sudo] password for haris: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by Terl on 2009-12-08
How did you install it?  How did you uninstall it?  You said "using commands"; what do you mean?  I installed Cairo dock through synaptic and it is in accessories and yours is in system tools.  If you did not use synaptic to remove maybe give that a shot...

---

### Post by Haris-MV on 2009-12-08
I installed From the Repository

---

### Post by ukripper on 2009-12-08
Try this :
```
sudo dpkg --remove --force-remove-reinstreq cairo-dock cairo-dock-plug-ins
```

---

### Post by Terl on 2009-12-08
Got it.  Using synaptic, look and see if you still have cairo-dock-core and cairo-dock-data installed.  If so remove those two and the whole thing will be gone.  I just tried it.  I first uninstalled cairo-dock and was left like yours.  Went back and found those other two.

Apparently, when you select it to be removed it misses those two pieces....

---

