---
title: "Grub loads old kernel after update??"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by pointyblue on 2008-12-28
Hi,

Just upgraded from 8.04 to 8.10 (dualboot with XP). But instead of making the new kernel default, Grub still loads the old kernel unless I manually choose the new one.

How do I fix that?

:)

---

### Post by ercferret18 on 2008-12-28
```
sudo nano /boot/grub/menu.lst
```

find something like "default" and change it to the line you want made default (the first line is 0)

---

### Post by Michael.Godawski on 2008-12-28
hi,

this guide can be easily changed to your needs. Originally it was written to set windows as default in grub, but you can use it and change it to your needs:


[LIST]
[*][http://godawski.oxyhost.com/setwindowsdefault.html](http://godawski.oxyhost.com/setwindowsdefault.html)
[/LIST]

---

### Post by fooman on 2008-12-28
startup manager has option which lets you choose which kernel/os to boot from....and many other useful items to configure.  it is available in synaptic (search for startupmanager) or from a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

---

### Post by pointyblue on 2008-12-29
Thanks to all of you for helping out!  ):P

I used the startup manager to fix the problem.

:)

---

