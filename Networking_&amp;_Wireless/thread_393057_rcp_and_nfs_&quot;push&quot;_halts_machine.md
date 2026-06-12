---
title: "rcp and nfs &quot;push&quot; halts machine"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by perstromgren on 2007-03-25
The other day I got a problem with copying files from one linux machine ("desktop") to another ("archive"). I have had this working for a long time, but something have happened, I do not know what.

At any rate, I can't copy a file from "desktop" to a an NFS-mounted volume residing on "archive"; if I do, "desktop" freezes. It does not respond to anything, not keyboard, mouse or ping. The only way out is to hold down the power button (is this a reset, perhaps?).

If I 

[FONT="Courier New"]desktop> rcp foo.jpg archive:foo.jpg[/FONT], 

same thing happens, "desktop" halts.

[FONT="Courier New"]destop> ssh archive[/FONT]

works fine.

Both desktop and archive are continously updated, and up to date now. The NFS traffic has been working fine for six months. "archive" exports the same volume to a Windows box, and this communication works as intended.

I have searched the bug lists, but I cannot find anything similar. 

Has anyone seen this?

---

