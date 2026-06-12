---
title: "how to reconfigure graphics in jaunty"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-07-20
i tried to change my screen resolution to test some work of mine 
somthing went wrong so i ended up rebooting 
trying to be clever i tried recovery xfix from grub menu
now jaunty wont boot x
i tried 
root terminal
dpkg-reconfigure xserver-xorg
that just asked me for keyboard settings 
how can i reset my graphics driver
i want  to die my work is overdue already:(

---

### Post by PmDematagoda on 2009-07-20
What graphics card are you using?

---

### Post by doomsword2001 on 2009-07-20
**for what i say i am not totally sure so act at ur own risk** :popcorn:

i guess changing resolution means editing /etc/X11/xorg.conf
if i am right when u edit that file, it creates a backup at dir /etc/X11/ something like xorg.conf.42342536574674

have you tried using live cd and replacing xorg.conf ?

---

### Post by Arthur Millar on 2009-07-20
> **PmDematagoda said:**
> What graphics card are you using?

 ati hd3870
i was using proprietry drivers

---

### Post by Arthur Millar on 2009-07-20
> **doomsword2001 said:**
> **for what i say i am not totally sure so act at ur own risk** :popcorn:

i guess changing resolution means editing /etc/X11/xorg.conf
if i am right when u edit that file, it creates a backup at dir /etc/X11/ something like xorg.conf.42342536574674



have you tried using live cd and replacing xorg.conf ?



i will give it a try

---

### Post by Arthur Millar on 2009-07-20
> **Arthur Millar said:**
> i will give it a try

no amount of xorg.conf configuring is having any affect 
i have tried the failsafe file with no luck also

---

### Post by Arthur Millar on 2009-07-20
well i guess this means another long night of updates and reinstalling 
ubuntu u suck

---

### Post by automaton26 on 2009-07-20
If you're using proprietary drivers (Catalyst?) then I don't think xorg.conf is relevant any more.

With my ATI 4850, I can run the ATI Catalyst Control Center by doing:

```
DISPLAY=:0 amdcccle
```

---

### Post by gjoellee on 2009-07-20
EDIT: Whoops...did not read your first post carefully enough :P

---

### Post by achase79 on 2009-07-20
have you set up xorg.conf for your video card using the "radeonhd" driver?  You may have to redo this by hand or if it is just as easy to reinstall the propriatory radeon driver.  This should return your diplay to before you tried to change the resolution.

---

### Post by Arthur Millar on 2009-07-21
thanks for the posts
but i have set up my pc in such a way that only programs and updates are lost on a reinstall 
it just seems that much easier than to post and wait and fiddle till all hours of the morning 
my set up is as follows 
ati hd3870 
using FGLRX
my display tab in system>preferences takes a long time to load for some weird reason, and catalyst can not apply any changes 
its all very delicate and as they say don't fix whats not broke  
its just a bit of an issue when you are trying to test web pages by resolution

---

