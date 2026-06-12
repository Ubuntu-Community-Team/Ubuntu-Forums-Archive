---
title: "Connect via samba"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by tr33m4n on 2008-11-04
Hello there,

I have setup samba on an ubuntu server on my network and windows can see it fine. The only problem I have is when I try to connect to it using the login details ive setup, xp appends my login name with the computer name and therefore I can't log in... Is this a samba issue or XP? anyone have any ideas on how to fix this?

Many thanks

Dan

---

### Post by Iowan on 2008-11-05
For what it's worth, I've seen that before - just can't remember where.  Seems like it was a few releases ago.  My _Samba Unleashed_ book is now 8 years old, and doesn't cover the new stuff, but I'll see if that pops up.

One crude method would be to use the username mapping, but it would be cleaner to find why/where the "appendage" is coming from.

Aside from */etc/hosts*, you might check */etc/resolv.conf*.  I doubt the answer is there, but won't hurt to check!

---

### Post by tr33m4n on 2008-11-05
No luck im afraid :( I'm leaning towards it being an issue with XP tho... just still no idea where to look :( Thanks for your help anyway

Dan

---

