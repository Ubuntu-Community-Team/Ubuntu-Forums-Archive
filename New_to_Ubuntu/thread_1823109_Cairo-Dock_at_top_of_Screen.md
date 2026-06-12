---
title: "Cairo-Dock at top of Screen"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by fslezak on 2011-08-11
This is an odd problem.

This morning, I loaded Cairo-Dock and I saw that it was stuck at the TOP of my screen!

I entered the Cairo Settings and I saw that it was set to bottom.

I tried everything (including purging Cairo Dock and installing the beta) to no avail.

I like Cairo, and I dislike that it is stuck at the top of my screen.

Info:

Intel 82852/855GM Graphics Card
OpenGL option enabled
Metacity Compositing
No Compiz (Destroys my Graphics Card)


Please help me solve this problem!!!

---

### Post by fslezak on 2011-08-11
I also noticed that Cairo makes a space at the bottom for the dock, but stays at the top. I am attaching screen shots of it in 'bottom' mode and 'right' mode.

Any help is greatly appreciated.

---

### Post by MG&amp;TL on 2011-08-11
Don't have a clue about Cairo (I like it too), but you could try a different dock, there's plenty out there. Docky is in the repositories, I think. To me, one is very like another. Oh, and you did try 'applying' the 'set to bottom' thing?

---

### Post by ~!geek!~ on 2011-08-11
With the latest cairo dock available in ubuntu 11.04 repository, you may right click the dock -> select cairodock option -> click on configure option -> advanced mode and play around with the behavior tab to manage the position and all those stuff. But as you mentioned you purged and reinstalled cairo dock, So I am afraid it will be of any help to you. Still give a try.

---

### Post by corncob on 2011-08-11
You did reboot the computer?

---

### Post by fslezak on 2011-08-11
Tried everything above. I played with the settings, even.

The only reason I like Cairo is that it is VERY customizable.
AWN is good, it is just featureless in terms of launchers.
Docky again is good, but it has no extras like Cairo.

Reboot the computer?!? Only fourteen times!

This problem happened after ~3 days after purging GNOME 3 (bad Graphics Card).
I even managed to delete the config files for Cairo.

---

### Post by ahgblopes on 2012-06-04
Maybe a problem with metacity properties in gconf?

I'm using cairo-dock with metacity compositor. After i change /app/metacity/general/disable_workarounds to true, i get the same problem (dock at the top of the screen). After i changed it to false again, the problem was solved.

---

### Post by Enigmapond on 2012-06-04
Try AWN (Avante Window Navigator...much better than Cairo and easier to configure with more options.

---

