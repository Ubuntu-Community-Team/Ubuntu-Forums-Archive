---
title: "helpppppp my update manager, synaptic etc has broken!!!"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by antoinettey on 2009-10-09
wen i try to access my synaptic package manager this comes up

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

the same message also comes up whenever I try to run my update manager

i think i know why this has happened a few days ago i opened my computer janitor and clicked on the clean-up button and it may have taken off some files that are needed for file sharing or something? please help my computer is failinggggg badly, initally i would love to just wipe my computer and restart but i dont know how ta do this either....

---

### Post by wojox on 2009-10-09
Open the terminal and run:

```
sudo dpkg --configure -a
```

---

### Post by Love2MeetU on 2009-12-07
> **wojox said:**
> Open the terminal and run:

```
sudo dpkg --configure -a
```

I have a similar problem right now, tried what you suggest but it's just hanging there with
[I]
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.31-14-generic/updates/dkms/nvidia.ko[/I] 

Does nothing else. Still not fixed.

---

### Post by The_Pirate_King on 2009-12-07
It seems to me that there are some serious problems with the newest release of "apt", Ubuntu's package installer.  I experienced a very similar issue when trying to install Adobe Flash Player.  
Did you recently install any new software?

---

### Post by k3lt01 on 2009-12-07
.....

---

