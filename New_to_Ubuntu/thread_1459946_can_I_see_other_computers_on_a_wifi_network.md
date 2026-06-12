---
title: "can I see other computers on a wifi network?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by kapi on 2010-04-22
Hi and good morning to you.

I've looked at several youtube vids relating to Samba and seeing other computers on my network but I can't seem to see any.

I'm using wifi does that make a difference or does everything have to go via ethernet?

I've installed Samba and it appears to be working ok, Ive made a pictures folder set to share on a workgroup I set up and that seems to be OK to, it's when I open windows xp( sorry for swearing LOL) and select networks that nothing comes up.

Any ideas? these forums have been an absolute God send, I hope we can sort this one out.

---

### Post by gradinaruvasile on 2010-04-22
Wired or wireless is not important, its treated by programs the same way.
There may be one catch: if more than 1 computers are connected to the same access point make sure it is configured to let computers see each other (although by default this option is on).

What is important: you must have a working samba setup. Try reaching your computer by its IP address.

---

### Post by kapi on 2010-04-22
Thankyou very much, will do that now.

Craig

---

### Post by 3rdalbum on 2010-04-22
I believe both computers need to have the same workgroup name; I think Ubuntu defaults to "WORKGROUP" and Windows defaults to "MS_HOME".

Windows XP doesn't seem to be as easy to use to access Samba shares, IMLE.

---

