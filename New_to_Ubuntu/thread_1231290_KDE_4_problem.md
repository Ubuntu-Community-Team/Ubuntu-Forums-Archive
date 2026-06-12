---
title: "KDE 4 problem?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by gasmansteve on 2009-08-04
Hi all
Just installed Ubuntu 9.04 everything recognised and works fine. Thought I`d have a go with KDE 4 so installed it then rebooted and for some wierd reason the ruddy default screen resolution is now 320x200 and I cant alter it so had to do a complete reinstall.
I could access the terminal so if it does it again is there a `Go back` facility like in windows or can I do something in terminal?
Cheers
Steve

---

### Post by blazemore on 2009-08-04
Well what seems to be happening is that KDM is loading instead of GDM, which is somehow breaking your resolution.
How did you install KDE?

To change between GDM and KDM (Both can load Gnome and KDE)
run the command
```
sudo dpkg-reconfigure gdm
```
or
```
sudo dpkg-reconfigure kdm
```

---

### Post by gasmansteve on 2009-08-04
Hi blazemore

How did you install KDE?

Just used the Ubuntu installer, no probs installing other packages. Maybe best to stick with Gnome for  now, PIA reinstalling the full system again. Shame as I used to prefer KDE a couple of years ago and KDE 4 screenshots seem pretty slick maybe do it when 4.5 comes out :D.
Regards
Steve 


__

---

### Post by gasmansteve on 2009-08-04
> **blazemore said:**
> 
How did you install KDE?

To change between GDM and KDM (Both can load Gnome and KDE)
run the command
```
sudo dpkg-reconfigure gdm
```or
```
sudo dpkg-reconfigure kdm
```

Just used the Ubuntu installer, no probs installing other packages. Maybe best to stick with Gnome for now, PIA reinstalling the full system again. Shame as I used to prefer KDE a couple of years ago and KDE 4 screenshots seem pretty slick maybe do it when 4.5 comes out :grin:.
Regards
Steve

---

