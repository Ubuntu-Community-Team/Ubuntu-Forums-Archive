---
title: "Set primary monitor"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by lawrencegoodman on 2010-04-20
I am using Lucid with kernel 2.34.rc5 because I need support for a multi touch monitor.

I now want to make the multi touch monitor my primary monitor. There is no xorg.conf file to edit, just these: /usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf

Can someone provide some clear instructions on how to do this? I would be very grateful.

Thanks.

---

### Post by jvc26 on 2010-04-28
Hi Lawrence, just as a brief question, can you not do that through the Monitor Settings dialog System->Preferences->Monitors? (I must admit its been a while since I used multiple monitors so I may be a little outdated!)

Alternatively, you can use xrandr (I'm sure there is probably a newer method than this!)

```
xrandr primary <output>
```

See

```
man xrandr
``` 

for more information.

Hope that helps,

J

---

### Post by sean_worker on 2010-04-30
the syntax for xrandr would be:
```
xrandr --output LVDS1 --primary
```
(assuming when you run:
```
xrandr -q
```
without the external monitor connected, that the name of the built-in display is LVDS1)

I currently have a problem with --primary not having any effect.
If I put the external monitor, VGA1 for my video card, above or left-of my laptop screen, the external monitor will always be the primary (at least it will have the xfce panel).
If I put the external monitor below or right-of the laptop screen, the laptop screen will always be primary.
It doesn't matter whether I set one of the monitors as primary, it seems to have no effect.

---

