---
title: "Exit X Server in Jaunty"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jaygeebuntu on 2009-10-22
How do I exit the X server when using Ubuntu 9.04?

---

### Post by LewRockwell on 2009-10-22
> **jaygeebuntu said:**
> How do I exit the X server when using Ubuntu 9.04?

[http://ubuntuforums.org/showthread.php?t=1040988](http://ubuntuforums.org/showthread.php?t=1040988)

more historical reference

[http://forums.linuxmint.com/viewtopic.php?f=151&t=21575](http://forums.linuxmint.com/viewtopic.php?f=151&t=21575)

.

---

### Post by jaygeebuntu on 2009-10-22
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=1040988](http://ubuntuforums.org/showthread.php?t=1040988)

more historical reference

[http://forums.linuxmint.com/viewtopic.php?f=151&t=21575](http://forums.linuxmint.com/viewtopic.php?f=151&t=21575)

.

Many thanks. Maybe I'll now be able to install the nvidia driver.

---

### Post by falconindy on 2009-10-22
Tinivole posted a great how-to on installing nvidia drivers manually. Make sure to read through it to the end and create the update script to handle kernel updates.

[http://ubuntu.ubuntuforums.org/showthread.php?t=1125400](http://ubuntu.ubuntuforums.org/showthread.php?t=1125400)

---

### Post by sandyd on 2009-10-22
> **jaygeebuntu said:**
> How do I exit the X server when using Ubuntu 9.04?
```

sudo killall gdm
sudo killall kdm

```

---

### Post by jaygeebuntu on 2009-10-23
Hi falconindy

Thanks for the link which I fear I may have to follow to get desktop effects enabled with my GeForce FX5200 video card.

Hi carlee

entering "sudo killall gdm" finished up on a mono text screen that froze at a "checking battery state.." line.

Background
----------

I can't get desktop effects enabled using the installed nvidia 173.14.16 driver so I'm trying to install the nvidia 173.14.18 driver instead. Unfortunately this requires that I exit the X server and switch to runlevel 3 state.

Keying CtrlAltGr+SysReq+k still keeps me in a graphical environment and doesn't allow the nvidia install to work.

I've got no probs enabling desktop effects in Fedora 11. Maybe I should just wave goodby to Jaunty if I can't even get into runlevel 3.

---

### Post by tarps87 on 2009-10-23
```
sudo /etc/init.d/gdm stop
```

Ubuntu has a nasty habit or restarting x ;)

---

### Post by 3rdalbum on 2009-10-23
> **jaygeebuntu said:**
> Hi falconindy

Thanks for the link which I fear I may have to follow to get desktop effects enabled with my GeForce FX5200 video card.

Hi carlee

entering "sudo killall gdm" finished up on a mono text screen that froze at a "checking battery state.." line.

When you get to that line, press Control-Alt-F2 and you will have access to a new terminal console where you can log in.

---

