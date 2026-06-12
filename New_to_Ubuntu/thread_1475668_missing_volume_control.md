---
title: "missing volume control?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by listerdl on 2010-05-07
Hi can someone kindly reach out and tell me why I am missing volume control on the panel? Normally I simply Add to Panel but there donest seem to be a volume option?

Thanks!!!!!!!

---

### Post by bikeboy on 2010-05-07
Do you have the "indicator applet" on your panel?

---

### Post by listerdl on 2010-05-07
THANKS!!!!!!!!!

All done!

That worked

---

### Post by inameiname on 2010-05-07
If you want it the way it was in Karmic:

I found this when I was in search of a resolution to the same problem.  And it seems to work:

                                 go to System > Preferences >  Startup Applications

in the startup tab, look for 'Volume Control' and check it if its  unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

---

