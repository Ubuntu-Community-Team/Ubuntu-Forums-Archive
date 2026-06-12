---
title: "Make a WRITE ONLY shared folder"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by SimoneB on 2008-09-17
Hi,
I have a shared folder named "Public". It works perfectly, I can see it from all the computers in my network.
I thought I could use another folder, named "Private", inside the "Public" one, except that it would have write only permissions; so that other clients could write files there but not read what's in it.

That looked easy: just create a "Private" folder inside the "Public" one, chmod to 733 (rwx-wx-wx)... but it doesn't work. If I try to put a file there from a remote computer, it says permission denied. (I tried also 722, without the "x" permission)

What's wrong? Is SMB that does not allow this behaviour?

---

