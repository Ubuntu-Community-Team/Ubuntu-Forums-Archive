---
title: "[SOLVED] Hardy Install"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-09
Good Morning,
I began the install upgrade last night from 7.10 to 8.04. This morning after the install was finished I was given the option of re-starting the computer or cancel... Opps,  I accidentally clicked on the wrong tab. When I tried Sys>Admin>UpgradeMgr it reflects my system as updated & of course, no longer offers the upgrade option to 8.04. I have tried to download the upgrade to a CD version several times & always get some type of error in the burn. Is there anything I can do to allow the computer to allow me the upgrage without starting from the 7.10 CD again.

---

### Post by Michael.Godawski on 2009-01-09
hi,
which options do you get when you run this in terminal?
```
gksudo update-manager -c -d
```

edit:

I would always recommend a fresh install.
Have a look here when you encounter errors on your cd:

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> hi,
which options do you get when you run this in terminal?
```
gksudo update-manager -c -d
```

edit:

I would always recommend a fresh install.
Have a look here when you encounter errors on your cd:

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

cocoknots@cocoknots-laptop:~$ gksudo update-manager -c -d
gksudo: invalid option -- c
GKsu version 2.0.0

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> hi,
which options do you get when you run this in terminal?
```
gksudo update-manager -c -d
```

edit:

I would always recommend a fresh install.
Have a look here when you encounter errors on your cd:

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

When I entered the '-d' option I received this:

cocoknots@cocoknots-laptop:~$ gksudo update-manager -d
No ask_pass set, using default!
xauth: /tmp/libgksu-wrYTId/.Xauthority
STARTUP_ID: gksudo/update-manager/7890-0-cocoknots-laptop_TIME1880146
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: update-manager
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
cocoknots@cocoknots-laptop:~$

---

### Post by Michael.Godawski on 2009-01-09
my fault.

try without the gksudo.
just ```
update-manager -d
```

---

### Post by CoCoKnots on 2009-01-09
> **Michael.Godawski said:**
> hi,
which options do you get when you run this in terminal?
```
gksudo update-manager -c -d
```

edit:

I would always recommend a fresh install.
Have a look here when you encounter errors on your cd:

[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

> **Michael.Godawski said:**
> my fault.

try without the gksudo.
just ```
update-manager -d
```

Thanks Michael, That worked a little better... except it is offering an upgrade to 8.10. I didn't think I could jump from 7.10 to 8.10... Is this correct ?

---

### Post by CoCoKnots on 2009-01-09
This is interesting... I shut down the computer manually & re-booted. I then checked: Sys>Admin>SystemMonitor>System & it shows I am using 8.04... It looks like the upgrade was successful after all. Thanks.

---

