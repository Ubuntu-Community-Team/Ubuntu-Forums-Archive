---
title: "Mystical XKB Error On Startup"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by bsonk on 2009-04-11
I don't know what this means or how it affects me. If it doesn't, I'll just ignore it. I'm on an MBP and I that there were some MacBookPro keyboard issues (someone's ctrl key). Is this similar?

I get this message on startup:

Error activating XKB configuration.
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

---

