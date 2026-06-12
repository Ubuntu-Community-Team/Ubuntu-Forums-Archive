---
title: "How do you change log-in screen on 9.10?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-11-01
The Log-in theme window seems to have disappeared in 9.10 (the one that lets you choose login start up screen) is there anyway to reinstall it or select it in 9.10?

---

### Post by ranch hand on 2009-11-01
The login box is pretty well set as is.

The background image is changable.

The xsplash comes up first, then GDM, then xsplash.  This is after the usplash (black background with white Ubuntu logo).

The images for xsplash live it /usr/share/images/xsplash.  There are 7 "bg" images.  Pick your image and run it through gimp to match the size and resolution of the default images and replace them.  The GDM uses the bg_2560x1600.jpg image.

I use my wallpaper as the menu background (grub2) and the xsplash/GDM image.

There is no GUI yet but I like it the way it is because I can, potentially, use ANY image I want.

---

### Post by Nightstrike2009 on 2009-11-03
> There is no GUI yet but I like it the way it is because I can, potentially, use ANY image I want.

Thats what i mean Ranchhand in jaunty you had a option from the top panel bar to view & change login background & appeareance but it seems to have disappeared in karmic, any ideas on how to put it back in?

Not really interested in terminal workarounds, iam new(ish) and not that confident with terminal commands. :(

---

### Post by ranch hand on 2009-11-03
I am afraid that you may have to wait for 10.04, at least that was pretty much the opinion of folks on the testing forum.

---

