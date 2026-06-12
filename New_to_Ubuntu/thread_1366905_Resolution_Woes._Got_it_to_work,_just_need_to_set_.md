---
title: "Resolution Woes. Got it to work, just need to set it every time"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by BOBSONATOR on 2009-12-28
Hey guys, Just installed karmic on my friends father's computer that has an intel integrated graphics card. Has some cheap-o lcd monitor that didnt detect resolutions, so I forced it using the following commmands

```
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```
```
xrandr --addmode VGA1 1680x1050_60.00
```
```
xrandr --output VGA1 --mode 1680x1050_60.00
```

Can someone lend me a hand and show me how to do this everytime i login/startup?

Thanks!
(im loving karmic btw)

---

### Post by sharaq on 2010-01-02
try this link post #6
this will make it permanant
if not you can add the ```
$ cvt 1680 1050
```
output of (modeline) to the xorg.conf and make it permanant. 

[http://ubuntuforums.org/showthread.php?t=1364460]("http://ubuntuforums.org/showthread.php?t=1364460")

---

