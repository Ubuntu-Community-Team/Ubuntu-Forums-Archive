---
title: "Title bar on all windows have glitches after enabling graphic drivers"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by MockY on 2009-02-26
This has only happened to me in Ibex, and that with Nvidia cards in both the 6 series and the 8 series using any of the 3 provided drivers in Hardware Drivers manager. Please note that it only occurs when the desktop visual effects is set to Normal or Extra.

So what happens. Well, the title bar on any open windows gets glitches when the mouse is hovered over it, resulting in what the attached picture shows.

How can I prevent this prom happening? I would like to be able to use at least some desktop effects.

---

### Post by nicoverbking on 2009-02-26
I'm using the latest driver provided in Intrepid and using a card from the 8-series and I don't have this problem.

You might want to try and change some of the settings in CompizConfig, and see if that helps.

Or, perhaps the problem is Metacity (window decorator). Have you tried the Emerald window decorator? If that one displays correctly, the problem is Metacity.

Reloading your theme might help too.

---

### Post by MockY on 2009-02-26
I manually installed the drivers provided by Nvidia (the 180.29 drivers) and the problems went away. Why aren't these drivers available vis the Hardware Manager I wonder.

---

