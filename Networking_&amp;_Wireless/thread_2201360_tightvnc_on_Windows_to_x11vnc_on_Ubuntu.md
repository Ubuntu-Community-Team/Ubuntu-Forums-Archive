---
title: "tightvnc on Windows to x11vnc on Ubuntu"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by yilduz on 2014-01-24
First of all, I was considering posting this in the "Absolute Beginners Section" because I'm very new to Linux, but this section seemed a bit more appropriate. Just, please keep that in mind.

So I have a computer plugged into my television which I use for streaming and stuff like that. I've always used TightVNC to control that computer from my laptop. Recently Windows on the computer died, so I partitioned the drive and installed Ubuntu, but I wanted to get the VNC going again. I have TightVNC on the laptop, and x11vnc on the desktop connected to the television. Everything is "working" but there just seems to be a minor issue in the settings that I cannot figure out. When I launch TightVNC on the laptop, all I see is the wallpaper over the Ubuntu box. I don't see its dock, the toolbar on the top, any windows that are open on the Ubuntu box, or anything at all. Just the wallpaper. It seems to act as a completely separate box and acts independently of the actual Ubuntu machine, but I want to see and control what is being displayed on the television.

Can someone please help me with this?

edit: A bit o' troubleshooting. I tried installing tightvncserver on the Ubuntu machine, and also tried RealVNC on the Windows machine. Regardless of the viewer/server combination, it has the same results.
edit 2: Looking around, this may not have been the best board for this question.

---

### Post by steeldriver on 2014-01-24
What version of Ubuntu and what desktop? The ubuntu-3d (compiz based) desktop sometimes misbehaves with VNC

x11vnc *should* do what you want, however if you installed the regular desktop version of Ubuntu, then you can use the built-in 'Desktop Sharing' app (vino-server) - just type 'Desktop Sharing' in the dash area or run 

```

vino-preferences

```

in a terminal.

FYI tightvncserver is usually used to create separate X sessions rather than share/relay an existing desktop session - so that's probably not what you want.

---

