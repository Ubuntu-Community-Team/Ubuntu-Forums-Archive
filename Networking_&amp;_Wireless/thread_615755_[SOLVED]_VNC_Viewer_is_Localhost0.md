---
title: "[SOLVED] VNC Viewer is Localhost:0"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by apple_and _linux on 2007-11-17
Hey, I just helped a friend install Gutsy over the phone.  However, now he is having some difficulties and I'd like to use Remote Desktop to access his computer.  However, his vncviewer address is localhost:0
Why is this and how do we change it?  Thanks!

---

### Post by eldragon on 2007-11-17
to begin with.....

if your friend is behind a router/nat he should forward the port 5900 to his LAN ip

then you should try to connect to his internet IP (make him go to [www.whatsmyip.org](www.whatsmyip.org))

that should be it.

---

