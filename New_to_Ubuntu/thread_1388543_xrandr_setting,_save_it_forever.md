---
title: "xrandr setting, save it forever?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-23
How do I either save the xrandr setting forever, or have the following command execute at startup without having to use a gnome/xfce/kde app?

```
xrandr -s 1024x768
```

I hate the huge resolution it has by default: 1400x1050.

---

### Post by diesch on 2010-01-23
See [https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently)

---

### Post by Psumi on 2010-01-23
Thank you. Putting:
```
xrandr --output LVDS --mode 1024x768
```

in **/etc/gdm/Init/Default** before the line
```
initctl -q emit login-session-start DISPLAY_MANAGER=gdm
```

works :3 But sometime I'll have to use the .xprofile method or something as I won't use gdm in the future.

---

