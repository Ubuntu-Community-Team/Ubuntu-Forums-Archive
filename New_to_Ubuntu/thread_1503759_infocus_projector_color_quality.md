---
title: "infocus projector color quality"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by expatCM on 2010-06-07
I am running an infocus projector from an nvidia graphics card.  The colors when I play a movie are really disappointing.  I have been looking round google and see that there is some mention of this but not too many solutions.

One possible solution appears to be to edit .bashrc and add

 alias ss='startx -- -depth 24 

This increases the color depth and should improve the color.  Or so I read.

I have not tried this yet since I was wondering if there are any other suggestions to fix this?

---

### Post by expatCM on 2010-06-10
The solution for me was to upgrade mplayer using the PPA.  Apparently the version of mplayer in synaptic is not the latest and the PPA installed an update which fixed the problem .......

---

