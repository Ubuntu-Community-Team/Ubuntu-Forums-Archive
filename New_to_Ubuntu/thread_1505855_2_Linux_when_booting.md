---
title: "2 Linux when booting???"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by ManfredKlinglmair on 2010-06-09
Hi,
I have a problem that's more a nuisance actually:  after installing Ubuntu 10.4 two days ago (fresh from Windows XP), and the getting all the updates for the fresh system as usual, now I have TWO options for Linux/Ubuntu when booting the system:
one is 'Kernel Linux 2.6.32-21 generic",
the other (obviously up-to-date-one) is 'Kernel Linux 2.6.32-22 generic'.

My question is, how do I get rid of the outdated (if that is correct) option? This is kind of annoying.

Thanks!

---

### Post by The Cog on 2010-06-09
Once you're happy the new version is working for you, you can remove the old one with synaptic: System->Administration->Synaptic, search for linux-image-2.6, mark the old one for removal, then apply.

---

### Post by TheForumTroll on 2010-06-09
In my opinion one should always have at least one older 100 % working kernel to go back to if something ugly shows its face with the new one ;)

If you don't want to pick one each time you can make it skip the menu at boot unless ESC is pressed or set a short timeout.

---

### Post by ManfredKlinglmair on 2010-06-09
Oh, I'm still trying out Ubuntu so far - so no sensitive data yet :)

And I like it (except for a few glitches).

Btw, it worked. Thanks!

---

