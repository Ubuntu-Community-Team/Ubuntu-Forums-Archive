---
title: "tint2 pops up"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by dzon65 on 2011-01-27
I have tint in my openbox autostart file (openbox session), not in my gnome autostart. Yet, it pops up in a gnome session as well. Any ideas?

---

### Post by dzon65 on 2011-01-27
This is weird. I deleted tint2 in my ~/.config/openbox/autostart.sh and it doesn't show in a gnome session anymore. Somehow tint2 is being mixed between the two autostart files.

---

### Post by thil77 on 2011-01-27
I suspect you are using openbox windows manager in gnome.
so openbox run the autostart command.

---

### Post by dzon65 on 2011-01-27
I am, but this a fusion setup. When I use compiz, tint's still there (even after reboot aaand worse, in compiz, tint2 even overrules lxpanel). Furthermore, if running openbox as wm in gnome, shouldn't the other openbox autostart settings apply as well? For exmple, nitrogen is set as nitrogen --restore &. Those settings don't apply when in gnome. This tint thing is the only one taken over. By gnome-settings-daemon maybe, i don't know.
Screenie when running compiz, tint placing itself on top of lxpanel.

---

### Post by thil77 on 2011-01-28
basically, tint2 can't autostart itself.

so tint2 is called in one of your autostart script.
check your gnome System > autostart menu...

---

### Post by dzon65 on 2011-01-28
Trust me, it isn't. Did some searching and it's probably the gnome-settings-daemon.

---

