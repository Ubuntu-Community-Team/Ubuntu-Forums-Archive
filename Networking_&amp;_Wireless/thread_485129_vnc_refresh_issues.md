---
title: "vnc refresh issues"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-06-26
i use xvnc4server and it will not properly refresh despite using deferUpdate 0 as an option.  I tries with xvnc4viewer and the viewer used by Terminal Server Client as well as from a Vista machine with latest realvnc viewer.

I have heard similar stories...seems like a common issue, but is there a solution?  I have read "solutions" that recommend using another vnc server which i do not want to do.

---

### Post by himuraken on 2007-09-13
I am having the same exact issue. I am testing with x11vnc and whatever the built in Ubuntu standard is (From X). I have used the latest versions of RealVNC, TightVNC, and UltraVNC with the same results each time. I successfully connect and get an image of the desktop. From there, nothing responds within the viewer. I know that the connection is working because I can sit next to the VNC server and watch the local screen update while my remote client will not. Any help is greatly appreciated.

Thanks

---

### Post by krunge on 2007-09-13
For x11vnc try:

```
x11vnc -noxdamage ...
```

This seems to be a bug in Beryl window manager or the X server.
[http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

---

