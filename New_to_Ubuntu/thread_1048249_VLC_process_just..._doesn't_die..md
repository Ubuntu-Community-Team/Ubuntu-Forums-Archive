---
title: "VLC process just... doesn't die."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Muffinabus on 2009-01-23
Well, it does, but only if I kill it in the System Monitor after every time I use VLC.  I couldn't figure out what was going on last night until I opened up the System Monitor and saw at least 5 processes for VLC, all of which shouldn't have been there as I had closed the program properly.  I only noticed this because my sound stopped working with all the various VLC processes running, so it actually does cause a bit of a problem.  Anyone know why this might be happening, or how to fix it?  I've the latest version of VLC with Ubuntu 8.10 installed.

---

### Post by Muffinabus on 2009-01-23
Hmm...  I tried the Windows way of doing things, reinstalling the program, and that seems to have fixed it for now.  I'll report back if I've any issues!

---

### Post by mjheagle8 on 2009-01-23
did you click the x to close vlc?
if that doesnt work, check that the icon is not in the tray.
last resort: in terminal
```
killall vlc
```

---

### Post by dnRoyston on 2009-01-23
> **mjheagle8 said:**
> did you click the x to close vlc?
if that doesnt work, check that the icon is not in the tray.
last resort: in terminal
```
killall vlc
```
You can do this, but it's a hassle. You could set a launcher in your panel (assuming you can with your WM), but I still think it's strage that this happens. :\

I see you solved the problem with the "windows" way :D, but if it happens again, let us know, because I've never had that happen to me before.

---

