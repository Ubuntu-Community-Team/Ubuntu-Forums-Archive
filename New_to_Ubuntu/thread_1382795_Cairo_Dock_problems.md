---
title: "Cairo Dock problems"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by cartisdm on 2010-01-16
This is my first 10 minutes trying out the Cairo dock.  Since it's on my netbook I have a few minor screen resolution bugs but I'll work them out later.  I'm running a theme that I downloaded from [here]("http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html") and I think the dock is having some trouble picking up the icons but I can't figure out how to set my own icons for the ones that aren't loading.

In my screenshot you can see the Corbeille (trash) isn't loaded and the calendar (furthest on the right) isn't loaded.  How can I just assign them a new icon?

---

### Post by fabounet on 2010-01-16
seems like an opengl issue, try running the dock with
```
cairo-dock -oi
```

by the way you can configure any applet by right clicking on it -> Configure this applet

---

