---
title: "Xserver, disabling color depths/video modes"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Hospadar on 2008-12-24
I'm installing ubuntu (server) on an old machine I have and I'm putting fluxbox on top of the installation.

I've installed xorg and fluxbox (sudo apt-get install xorg fluxbox) and I'm trying to get X running (even without fluxbox)

When I try to start X (startx) it dies with this error: "AddScreen/ScreenInit failed for driver 0"

From googling around it sounds like this is caused by there being video modes which are too large or too much color depth.  In ye olden times I'd probably have gone into xorg.conf and edited out the higher video modes, but nowadays xorg.conf doesn't have that info and "sudo dpkg-reconfigure xserver-xorg" doesn't let me make those settings like it used to.

Where do I go nowadays do disable those higher video modes that I don't need (and which are probably preventing my system from loading properly)

On a side note: I know it's possible to make this work, my dad had originally installed a regular version of ubuntu on the machine and it did sort of load X, but this machine hasn't nearly enough power or memory to actually run ubuntu, so I switched to the server install.

---

