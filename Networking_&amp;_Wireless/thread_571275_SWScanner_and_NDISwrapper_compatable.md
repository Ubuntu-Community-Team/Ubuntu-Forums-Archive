---
title: "SWScanner and NDISwrapper compatable?"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Rockman4140 on 2007-10-09
After a very eye-opening experience compiling the new SWScanner from SVN (Makes you glad for packages, eh?) I got it running only to be stopped by this error message:

[SIOCSIWMODE] 1: Operation not permitted

Is this a Run as Root issue, or does using NDISwrapper limit my ability to scan with my Atheros AR5007EG card? I was hoping to turn my laptop into a wardriving/gaming powerhouse, but I may have to rethink that if it is a hardware issue.

If it is Run as Root, how would I do that? SWScanner doesn't work from the normal terminal like it should, and when pointing it to the program and typing swscanner, I get nothing. I apologize for my inexperience and if anyone could grace me with information, it would be valued.

---

### Post by jaygo on 2008-03-08
gksu swscanner
as seen here: [http://ubuntuforums.org/showthread.php?t=395265&highlight=swscanner]("http://ubuntuforums.org/showthread.php?t=395265&highlight=swscanner")

The problem seems to be that it doesn't run with ndiswrapper or perhaps without KDE, I can't tell. It does seem to be more than a permissions issue.

---

