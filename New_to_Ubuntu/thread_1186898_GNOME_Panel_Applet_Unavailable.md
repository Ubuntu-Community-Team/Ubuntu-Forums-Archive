---
title: "GNOME Panel Applet Unavailable"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by matthew.ball on 2009-06-14
Hey, I just tried to add the user switcher applet, but perhaps I removed something required because it doesn't appear to show anything except for a white line ...

I can't click on it to remove it, I was wondering if someone knew of an alternative method?

It has removed the logout/shutdown options from my main menu (I think? I'm not sure why they are missing otherwise), so it's slightly annoying :p

---

### Post by dje on 2009-06-16
try restarting the panel, press Alt + F2 and run:
```
killall gnome-panel
```

dje

---

### Post by UbuntuNerd on 2009-06-16
try this command in a terminal to reset your panels to default:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

