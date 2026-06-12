---
title: "Help Restore Screen Resolution"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by shivkumars on 2009-05-14
I have 19" wide screen monitor running at 1440 x 900 resolution. I was just playing around with Display settings and now I my screen  resolution is set to 800 x 640. I don't even get an option in "Preference --> Display" to set the resolution to native 1440 x 900. Please help me guys

---

### Post by goiggles on 2009-05-14
I think you need to goto

system>preferences>screen resolution

---

### Post by aeiah on 2009-05-14
see if there's a xorg.conf backup you could use. you should backup xorg.conf to avoid these problems but perhaps one was backed up for you automatically.

what graphics card do you have?

---

### Post by shivkumars on 2009-05-15
> **aeiah said:**
> see if there's a xorg.conf backup you could use. you should backup xorg.conf to avoid these problems but perhaps one was backed up for you automatically.

what graphics card do you have?

Thanks... I used the backup of xorg.conf... now everything is fine

Code used was 

```

sudo cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf

```

---

