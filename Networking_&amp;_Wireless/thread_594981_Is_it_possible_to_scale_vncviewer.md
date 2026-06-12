---
title: "Is it possible to scale vncviewer?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by evilregis on 2007-10-28
I'm remoting into a server with a higher resolution than the machine that I'm remoting in with.

When I'm at work and remote in I'm using Windows (PuTTY & TightVNC) and TightVNC gives me the option to scale the window.  I scale it down 75% for it to fit in my screen at work (no scrolling) and I've a similar setup here at home... however I can't figure out how (or if it's possible) to do the same thing using vncviewer.

I see -geometry in the man pages but that is only for the VNC window itself, not scaling down the session as a whole.

Anyone have any tips?

---

### Post by jfrorie on 2007-10-28
> **evilregis said:**
> I'm remoting into a server with a higher resolution than the machine that I'm remoting in with.

When I'm at work and remote in I'm using Windows (PuTTY & TightVNC) and TightVNC gives me the option to scale the window.  I scale it down 75% for it to fit in my screen at work (no scrolling) and I've a similar setup here at home... however I can't figure out how (or if it's possible) to do the same thing using vncviewer.

I see -geometry in the man pages but that is only for the VNC window itself, not scaling down the session as a whole.

Anyone have any tips?

neither vncviewer or xtightvncviewer appear to have a scaling option.  You load TightVNC which appears to be a separate package.


[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

---

