---
title: "xscreensaver: how that the monitor gets in standby after 30min?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-12
hello 
xscreensaver is nice for showing srcsaver, but all the time the monitor shall turns off.

Isnt there any ways to reduce consumtion?


```
 $ dpkg -l | grep xscreensa
ii  xscreensaver                         5.10-3                     Automatic screensaver for X
ii  xscreensaver-data                    5.10-3                     data files to be shared among screensaver frontends
 
```

---

### Post by 73ckn797 on 2009-12-12
Have you looked at System/Preferences/Power Management for the settings for being on AC power or battery power? (see attachment)

---

### Post by frenchn00b on 2009-12-12
> **73ckn797 said:**
> Have you looked at System/Preferences/Power Management for the settings for being on AC power or battery power? (see attachment)

well it is more complicated. I am running fluxbox. I have this as startup scripts:
```
Esetroot -m $HOME/.wallpaper
tilda  &
xscreensaver -no-splash & 

```

---

### Post by 73ckn797 on 2009-12-13
Can't help you in that.

---

### Post by frenchn00b on 2009-12-13
> **73ckn797 said:**
> Can't help you in that.

thank you anyhow

---

