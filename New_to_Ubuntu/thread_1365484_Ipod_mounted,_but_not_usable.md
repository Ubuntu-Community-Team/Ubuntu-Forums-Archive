---
title: "Ipod mounted, but not usable"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by chrisod on 2009-12-27
My Ipod (Gen 1 mini) has always just worked, no problems. last week I did a clean install of 9.04 after I gave up waiting for a fix on 9.10 killing suspend/resume on my laptop. Now I can't get the Ipod to work.

It mounts when I plug it in. It is there at media/IPOD.

However, none of the Nautilus actions follow, it doesn't open a window and Rhythmbox does not open. It does not create an Icon on the desktop either. Neither Rhythmbox nor Songbird can see the Ipod. GtkPod does see the Ipod, but I really really hate gtkpod so I don't want to use it.

Any ideas on what is happening? Like I said, this Ipod has always just worked going back to at least 8.04.

---

### Post by LuisGMarine on 2009-12-30
Best recommendation is give banshee a try hopefully it can pick it up.  Also do you have this podsleuth installed?  Having that package usually installed relieves a lot of problems with ipods.
```

sudo apt-get install podsleuth
```

---

