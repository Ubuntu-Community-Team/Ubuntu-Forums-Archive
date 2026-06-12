---
title: "Xlib:  extension &quot;NV-CONTROL&quot; missing on display &quot;:0.0&quot;."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Finalfantasykid on 2010-08-05
I am trying to get the temperature of my GPU via the terminal.  I am using the nouveau driver so I can't use the nvidia-settings, so I decided to use nvclock.

```

$ sudo nvclock -T
Xlib:  extension "NV-CONTROL" missing on display ":0.0".
nVidia Geforce Go 7900GS
=> GPU temperature: 53C

```

sometimes after I run that, my mouse icon dissapears, (but re-appears after I go to standby and wake it up).

How do I get rid of that error?

---

### Post by sandyd on 2010-08-05
> **Finalfantasykid said:**
> I am trying to get the temperature of my GPU via the terminal.  I am using the nouveau driver so I can't use the nvidia-settings, so I decided to use nvclock.

```

$ sudo nvclock -T
Xlib:  extension "NV-CONTROL" missing on display ":0.0".
nVidia Geforce Go 7900GS
=> GPU temperature: 53C

```sometimes after I run that, my mouse icon dissapears, (but re-appears after I go to standby and wake it up).

How do I get rid of that error?
```

gksudo gedit /etc/X11/xorg.conf

```
add
```

[FONT=monospace]Load "nv-control"

```
under the module section.
save and restart.
[/FONT]

---

### Post by Finalfantasykid on 2010-08-05
since Lucid does not require an xorg.conf I do not have one there.  Will it work if that is the only thing I have in the xorg.conf?

EDIT:  Ok I tried it both ways, but neither solved the problem.  I am still getting the error.  Is it possible I do not have this installed, or it does not work with the nouveau driver?

---

### Post by sandyd on 2010-08-06
> **Finalfantasykid said:**
> since Lucid does not require an xorg.conf I do not have one there.  Will it work if that is the only thing I have in the xorg.conf?

EDIT:  Ok I tried it both ways, but neither solved the problem.  I am still getting the error.  Is it possible I do not have this installed, or it does not work with the nouveau driver?
nv-clock seems to have issues with the neaveou drivers, since it was originally geared towards the nvidia propriety drivers

---

