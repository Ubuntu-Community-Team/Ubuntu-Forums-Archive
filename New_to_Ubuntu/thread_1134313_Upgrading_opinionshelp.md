---
title: "Upgrading opinions/help"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by phantom3113 on 2009-04-23
I'm sure there's millions of these type of threads today, so I figure I'll add mine to the pile :P

With 9.04 being released now, I'm not sure when/if to upgrade or not. Is there a suggested waiting period for upgrading? Also, if I do, is it recommended to upgrade via update manager, or live CD? I've heard mixed accounts, so I'm not sure. Finally, I have my hard drive partitioned into two (one for root or "/" and the other for /home). Upon upgrading (just mounting /home in partition editor) what can I expect to be different/same?

---

### Post by JoshuaRL on 2009-04-23
There's a lot of info out there about what has changed, so I won't go into that here.  But as far as updating, its up to you.  I've had a few small issues sometimes when doing a distro-update, and for full functionality without any issues, its suggested to do a backup and fresh install.  But if you'd like to just do a system upgrade, then you can do that no problem.  If your system hasn't informed you that its time to update, go to the terminal and do this:
```

sudo update-manager -d

```

PS  I'm torrenting off my copy right now!  Of course, I tweaked my install so far that its pretty unstable currently.  All the more reason to be happy for the Jaunty release though.

---

### Post by phantom3113 on 2009-04-23
I'll most likely be going with a fresh install, just thought I'd see what the opinion was. Plus, my update manager hasn't informed me of a new version yet (it's set to normal releases). With the differences though, I meant if I just mount my /home directory instead of formatting it.

---

### Post by JoshuaRL on 2009-04-24
> **phantom3113 said:**
> I'll most likely be going with a fresh install, just thought I'd see what the opinion was. Plus, my update manager hasn't informed me of a new version yet (it's set to normal releases). With the differences though, I meant if I just mount my /home directory instead of formatting it.

Well, as far as I know if you just mount it instead of wiping, then it should try to overwrite any files that coincide with its own, while leaving the rest alone.  But I might be wrong.  The other option (probably safer) is that you can use a different username, and so keep everything separate until you move things over.  Then you could just erase the old /home folder, easy as that.  Probably a good option if you ask me.

---

