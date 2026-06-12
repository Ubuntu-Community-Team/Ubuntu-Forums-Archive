---
title: "Trackpad is Wonky"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by insub2 on 2009-02-07
I have a fresh install of Linux Mint on my pal's laptop and I can seem to do anything because the the computer is perceiving clicks.  I'm not even touching the computer and it's clicking wildly.  I left the mouse of the menu button and the menu is flashing at an amazing and inconsistent rate.

The problem seemed to have accelerated.  I was able to install all the updates and do a few other things before it started being unbearable.  So I started looking through the xorg.conf to set the MaxTapTime to "0"--that being the way I turned off tap-to-click on my last ubuntu install.  But there wasn't anything for input devices there.

I got GSynaptic but it says I need to set "SHMConfig" to "true" in the xorg.conf or xf86config.  But, as you'll recall, there is no input devices listed in the xorg.conf and I don't know anything about the xf86config. Plus the commented text at the top of the xorg.conf says if I were to add it myself, it would get ignored because it's all done automatically by the server.

I'm not really sure what to do to fix this.  Any ideas?


***
Sorry to post about an issue with another distro, but I had the same problem while running off an Ubuntu live CD.:-?

---

### Post by insub2 on 2009-02-08
...
so System > Preferences > Mouse > Touchpad seems to have done the trick.

---

