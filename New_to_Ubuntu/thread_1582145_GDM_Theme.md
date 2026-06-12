---
title: "GDM Theme"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by SEECo on 2010-09-26
How to install a gdm theme in ubuntu 10.04

---

### Post by JohnHeikkila on 2010-09-26
So you want to know how to install GDM Themes, right?
There are like gazillion topics about this..
Plus this should be in 'Installation & Upgrades'.

Install Art Manager:
_sudo apt-get install gnome-art_
then you can find Art Manager at
**System &#8594; Preferences &#8594; Art Manager.**

---

### Post by sikander3786 on 2010-09-26
If you just want to change the wallpaper. This is the method I use.

```

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

```

Logout and you will see the appearance preferences. Select any background and click close. Log in and now unlink appearance preferences from startup by typing.

```

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by P4man on 2010-09-26
Old GDM themes no longer work in 10.04. If you saw some flashy greeter themes and youd like them in 10.04, then forget it. You can change a few things in the new greeter, but its not nearly as custimizable as the old one.

Easiest way to change images and stuff in the new greeter is using ubuntu tweak
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by jtarin on 2010-09-26
You can use GDM2 from a ppa

---

### Post by SEECo on 2010-09-27
Thank you john that was the thing wjat i needed.

---

### Post by Crazedpsyc on 2010-09-27
If you're interested in making one you can look at the default theme in /usr/share/gdm

---

### Post by SEECo on 2010-09-28
Thanks for that

---

### Post by SEECo on 2010-10-23
> **SEECo said:**
> Thanks for that

Hey, the very next day my os was burned can you tell me to how to install these in 9.10

---

