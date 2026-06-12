---
title: "VNC and Windows"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by SZF2001 on 2008-03-03
Would there be a way to do this? I don't know anything about VNC other than you can do remote access on a network with another computer and actually see what your doing (ssh won't cut it)...

The problem is though, is that on all these computer labs I don't have administrative rights (I might soon though if I ask the right people, won't abuse them of course), and these lab computers are Windows (Vista) and my server over yander is Debian.

Any newb guides or anything someone can help me with? I really don't have a clue.

---

### Post by chewearn on 2008-03-04
[Linky]("http://ubuntuforums.org/showthread.php?t=383053&highlight=ssh")

---

### Post by jhetrick62 on 2008-03-04
That may work, but I have experienced problems getting vnc to work properly for some reason on Gutsy.  That was before the link referenced though was posted, so it may work now.

I just loaded FreeNX and it did the trick just fine for me.

Jeff

---

### Post by The Cog on 2008-03-04
I believe that VNC servers are available for Vista now. RealVNC claims to work on Vista [http://www.realvnc.com](http://www.realvnc.com). You might need admin rights to install it, I don't know.

How about using the remote desktop client that comes with Ubuntu. Applications->Internet->Terminal server client. Choose RDP or RDPv5 (Can't remember which).

---

