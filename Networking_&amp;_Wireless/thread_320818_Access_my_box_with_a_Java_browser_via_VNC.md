---
title: "Access my box with a Java browser via VNC?"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Elpram on 2006-12-18
Hi, I used to have setup on xp with realvnc that i could simply visit my computers ip address (on port 80 no less, helped for at work) and use it to control my computer from essentiall any computer.  I'm looking for a similar setup with Ubuntu.

I've installed vnc4server and vnc-java, but can't figure out how to get it to run on display 0, and can't seem to access it outside of my computer.  If I run vnc4viewer desktop:2, i get my display (greyed out, because im using Beryl, but one thing at a time I suppose).

I've tried running [http://myip:5802/](http://myip:5802/) and 5902, i've also tried running the setting -httpport 80, but I haven't had much luck (and yes, I'm taking care of port forwarding on my router).

When I try running Xvcn4, it tells me:
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running


I've searched around, but without much luck.

Thanks,
Elpram

---

### Post by Elpram on 2006-12-18
Also, when I do vnc4config I get this error:

No VNC extension on display :1.0

---

