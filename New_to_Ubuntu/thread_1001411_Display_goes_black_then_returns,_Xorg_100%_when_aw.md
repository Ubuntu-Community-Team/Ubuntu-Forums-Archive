---
title: "Display goes black then returns, Xorg 100% when away..."
date: 2008-12-03
forum: New to Ubuntu
---

### Post by lazyart on 2008-12-03
Having some funky stuff happen, don't know how to troubleshoot.  Seems to be Xorg related.

Running 64 bit Hardy, AMD Opteron 165 dual-core with 4 gb RAM hosting a couple virtual machines.  Doesn't appear to be a memory/disk paging problem.  Occasionally while using the desktop (browsing web, email, open office stuff) my screens (dual monitors) will flash black for a second or two and then the desktop will return.  Usually it will flash a second or third time but things continue on.

Sometimes when I leave the machine unattended, I will come back to it and the screens have shut off (like they are supposed to after 10 minutes).  I shake the mouse or hit a key but no response.  So I go to my Windows box and use putty to get in via SSH.  Xorg will show 99-100% cpu usage.  Killing Xorg will allow me to get back onto my system.

I'm using Nvidia-glx-new for my FX5200 video card.  Thinking this was related to Compiz I disable desktop effects but still no help.  Screensaver is set to blank screen, so I don't expect that is the problem.  Any ideas?

Thanks in advance.

---

### Post by lazyart on 2008-12-26
Turns out my video card was failing, in case anyone else googles this..

---

