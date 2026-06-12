---
title: "how to backup xorg?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-03-19
I ran into some difficulty with a 1024X768 resolution that disappeared when I switched drives the other day, I fiddled around and got it working again but I'd like to backup my settings so if it should happen again I don't run into difficulty. I'm iffy on how exactly to go about that though. Which thing do I backup xorg, x11 or xrandr - and what would be the correct command line? I was nervous about editing xorg.conf when I first started with Ubuntu but now that seems somewhat easier for my poor little mind to grasp than the whole xrandr thing.

thanks much

myst

---

### Post by kestrel1 on 2011-03-19
Backing up xorg.conf should be good enough.
Just restore it back to the X11 folder & away you go if you have problems.

---

### Post by realzippy on 2011-03-19
..depends on what
*I fiddled around and got it working again*
means.
If you edited/created a xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

xrandr/monitor settings may have created the file
~/.config/monitors.xml

or do you use nvidia/ati drivers?

---

### Post by mystmaiden on 2011-03-19
Thank you for the replies. I didn't create a xorg.conf  and the machine just uses onboard graphics. I'll check for the monitors file. I wonder if I should generate a xorg.conf?

edited to add - I searched nautilus, there's no ~/.config/monitors.xml

---

