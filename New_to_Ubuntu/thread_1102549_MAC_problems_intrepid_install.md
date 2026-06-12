---
title: "MAC problems intrepid install"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by nynoah on 2009-03-21
I am trying to help a friend with his ubuntu install on his MAC.  There are a lot of little problems.  Is there a WIKI somewhere on how to resolve all the issues with using a MAC.  This is a modern MAC that is intel based.  Its a previous generation MAC book pro.

Problems so far.  Getting the R click to work easier.  Right now we have to press control and f11 and f12 at the same time.  Kinda a pain.  

Also I have TONS of problems with Synaptic running.  It goes grey screen all the time.  Its almost un usable.  

I also can not install deb packages.  They lock up.

I am also having a hard time installing new incons with the appearence manager.  I try to install one and it just shuts off.

The key board is getting a constant error when I boot up.

Plus other small things too

Any clue how to fix?

---

### Post by nynoah on 2009-03-21
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Ok this is the error that we get upon boot up.  Any way that you guys know to fix this.

---

