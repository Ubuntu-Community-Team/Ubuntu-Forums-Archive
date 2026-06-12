---
title: "HOW TO Enable Desktop Effects (Compiz) in Ubuntu Jaunty 9.04 w/ Intel Graphic Drivers"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by gymophett on 2009-04-27
In the new Ubuntu 9.04 Jaunty Jackalope, Intel graphic (video) drivers 965 (x3000 or x3100) are blacklisted so you cannot run Compiz thus your desktop effects cannot be enabled. There is a way to enable desktop effects, though this is not recommended because the drivers were blacklisted due to an error in xserver-xorg-video-intel and they will be whitelisted when the bug fill be fixed.

But if you want to use Compiz anyway, all you have to do is type this in a terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Then, you're done. Just go to your desktop preferences and change the effects to your liking! :D

I am not responsible for any harm to your computer (which will more than likely not happen).

---

### Post by suprman2020 on 2009-04-27
Thanks a lot. This works great.

---

### Post by chrisby on 2009-04-27
> **gymophett said:**
> In the new Ubuntu 9.04 Jaunty Jackalope, Intel graphic (video) drivers 965 (x3000 or x3100) are blacklisted so you cannot run Compiz thus your desktop effects cannot be enabled. There is a way to enable desktop effects, though this is not recommended because the drivers were blacklisted due to an error in xserver-xorg-video-intel and they will be whitelisted when the bug fill be fixed.

But if you want to use Compiz anyway, all you have to do is type this in a terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Then, you're done, and it works great! Just go to your desktop preferences and change the effects to your liking! :D

I would be cautious about saying it works great.  It was blacklisted because many people are having system freezes.

---

### Post by agim on 2009-04-27
Also, this allows the regular wm to be loaded, and then starts compiz, which is rather clunky. I know there is a better way.
Also, isn't this thread number 500 or so for this topic?

---

### Post by gymophett on 2009-04-27
> **agim said:**
> Also, this allows the regular wm to be loaded, and then starts compiz, which is rather clunky. I know there is a better way.
Also, isn't this thread number 500 or so for this topic?

I'm not sure. All I saw were "Desktop effects don't work in 9.04" and stuff. So I just decided to put this up to help everyone out. :)

---

### Post by gymophett on 2009-04-27
There is an alternative which may be safer. It was discussed by me in another thread.

[http://ubuntuforums.org/showthread.php?p=7159092#post7159092](http://ubuntuforums.org/showthread.php?p=7159092#post7159092)

It reverts the driver to the one it was in Intrepid.

---

