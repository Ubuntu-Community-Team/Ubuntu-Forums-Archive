---
title: "GLX-Dock problem..."
date: 2010-05-20
forum: New to Ubuntu
---

### Post by KdotJ on 2010-05-20
Hey I wonder if anyone can help me...

I installed GLX-Dock (aka Cairo-Dock) and played around with it. I messed around with the themes, which messed up some of the icons. For example the 'switcher' applet now has no icon, it's just a blank space in the dock.

I then uninstalled it and the re-installed it but the dock was still the same (i.e the way I had configured it) so I assumed my config files had been saved previously and re-used by the new installation.

So I then removed GLX-Dock via synaptic, along with the 'data' packages and all things related to the dock. I then re-installed GLX-Dock from the software centre, but still the same issue. It loaded up how I had previously configured it, along with the missing icons.


Does anyone have any ideas on how I can start from scratch again? And install the dock as default?


thanks in advance

---

### Post by Zyrtec on 2010-05-20
If it's keeping the config files, then you should do a purge. I'm guessing

```
sudo apt-get purge cairo-dock
```

---

### Post by KdotJ on 2010-05-20
Just tried, and I also delete the cairo-dock folder located in ~/.config

It worked, as in when I reinstalled it everything was all back to default. Except the icon for switcher is still missing :confused:

strange stuff, thanks for the reply nonetheless

---

### Post by -humanaut- on 2010-05-21
You might have to purge any plug-ins as well.

---

### Post by fabounet on 2010-05-21
it sounds more like a bug in your graphic drivers than a mess in the theme.

if you have some other invisible applets (like dustbin or clock) and have an ATI and are under Lucid, this is a know bug in the ATI free drivers.

---

### Post by KdotJ on 2010-05-21
> **fabounet said:**
> it sounds more like a bug in your graphic drivers than a mess in the theme.

if you have some other invisible applets (like dustbin or clock) and have an ATI and are under Lucid, this is a know bug in the ATI free drivers.

that is 100% exactly what I have... No dustbin/clock/switcher icons with an ATI graphics card under lucid. Thank you for the info!

---

