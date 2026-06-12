---
title: "Uninstalled Evolution, Left Over Pieces?"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-07-29
I uninstalled Evolution because I'm using Ubuntu on my main laptop only for video editing and don't need email.  The screenshot below is everything that's in Synaptic even though I uninstalled Evolution.  Is it okay to delete those or will that break my system?

This is on a Wubi install of 11.04, so even if it does break it I can fix it very easily.

[IMG]http://i56.tinypic.com/2i263cn.png[/IMG]

---

### Post by Megaptera on 2011-07-29
I'd be cautious about what you remove. Have a look at #2 here:
[http://ubuntuforums.org/showthread.php?t=353973](http://ubuntuforums.org/showthread.php?t=353973)

---

### Post by jerrrys on 2011-07-29
EDIT:  sorry wrong post...but since i find myself here:

Evolution can no longer be remover; at all.   use to be that evolution common could be remover and disable the desktop portion.  but no longer.

evolution (full) is also in gnome-core and still not be removed.

if you do your own build, evolution on the desktop can be remover only be a custom build starting with gnome-control-center.  this will still give you evolution data file, but not evolution-common. thus eliminated from the desktop.  evolution-date is necessary for gnome.

---

### Post by zeroseven0183 on 2011-07-29
You can remove it by
```
sudo apt-get purge evolution
```.

Then to see which other packages are still in-place, type ```
dpkg -l | grep -i evolution
```

You can remove them then but please spare evolution-data-server as I believe it would mess up your Gnome desktop.

---

