---
title: "gnome system tools"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by jmfal on 2009-06-19
hi, everybody. did a fresh install of jaunty 9.04, then i installed ubuntu-studio from synaptic,no problems, installed updates from update manager-security and upgrades have error--E:dpkg was intrrupted,you must manually run sudo dpkg--configure-a  to correct the problem
E:_cache-7 open()failed,please report
Do I need gnome system tools2.22.2 Obuntu4 since switched to studio?
If I do make it simple, I`m having problems with terminal commands

---

### Post by WhiskyChris on 2009-06-19
Hi,

I'm not sure where the link to system tools comes from but have you tried running the suggestion in the error message?

That is to type
```
sudo dpkg--configure-a
```
into the terminal and hit enter?

---

### Post by jmfal on 2009-06-19
re; whiskey chris
I forgot to mention that I tried that-command not found.

---

### Post by Michael.Godawski on 2009-06-19
yep, because it must be:

```
sudo dpkg --configure -a
```
don't forget the spaces.

---

### Post by WhiskyChris on 2009-06-19
> **Michael.Godawski said:**
> yep, because it must be:

```
sudo dpkg --configure -a
```
don't forget the spaces.

d'oh, sorry - should've spotted that

---

### Post by jmfal on 2009-06-19
re:m godawski
thank you, but? I get this-
processing triggers for initramfs-tools...
update-initramfs :generating /boot/initrd.img-2.6.28-13-generic
setting up python-support(0.8.7ubuntu4
Is that all I NEED TO DO??

---

### Post by Michael.Godawski on 2009-06-19
The command should solve all conflicts related to broken or half-installed packages. If this is all you need to do I cannot tell by now, but I would run the command ;).

---

### Post by jmfal on 2009-06-19
RE: M.GIGALSKY
What I`m asking is just by doing that it does it by it self or do I have to command it to run--remember im noobie

---

### Post by Michael.Godawski on 2009-06-19
Paste the command into the terminal and hit enter. Then behold what happens next.

---

### Post by jmfal on 2009-06-19
re:M GIDAWSKY
WHAT COMMAND?? -sudo dpkg --configure -a  already done is there anything else?

---

### Post by jmfal on 2009-06-19
by the whats a bean,look at me i got some beans

---

