---
title: "System hangs when laptop lid closed"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-08
Hey community,

I'm running Karmic 64 bit 9.10, and I've noticed that when I close my laptop lid and re-open it later, the power light is on with a black screen. Nothing will wake it up, and I have to restart every time I close my laptop lid. 

In power settings, I have it set to "blank screen" when laptop lid is closed on AC power.

Any suggestions would be greatly appreciated! :lolflag:

---

### Post by lavinog on 2009-11-09
What video card do you have? Are you using a proprietary driver?

---

### Post by asuastrophysics on 2009-11-09
It's an intel driver, I'm using the open-source version. 

```
lspci:
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

thanks for responding :popcorn:. do you think i should file a bug report?

---

### Post by lavinog on 2009-11-09
It looks like it is already filed:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445)

---

