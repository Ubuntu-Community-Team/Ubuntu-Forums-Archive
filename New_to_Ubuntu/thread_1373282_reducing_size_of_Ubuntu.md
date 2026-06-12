---
title: "reducing size of Ubuntu"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by trampintransit2 on 2010-01-05
I read a post ages ago, and just cant find it now. Something about reducing the size of the installed OS by changing the way Ubuntu stores update files.....does that make any sense to anybody?

---

### Post by phillw on 2010-01-05
Hi, yeah .. i know that feeling ;-)

```
 sudo apt-get *option*
```

Where *option* is ...

> **autoclean**: removes all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repo or that have a newer version in the repo).

**clean**: removes all stored archives in your cache - This means your system would have to re-download them if you re-installed a package.

**autoremove**: a whole different thing, this option makes apt look for packages that are installed as dependency of an already uninstalled package and removes them. This is used to clean up unused dependencies that remain on your system.

Hoping that's what you were looking for.

Regards,

Phill.

---

### Post by mocoloco on 2010-01-05
Your probably talking about the apt cache.  If you want to see how much space it's using do this in a terminal:
```
du -h /var/cache/apt/
```
It's not unusual for it to have several hundred megabytes or more.

Now, open Synaptic from System > Administration.  In synaptic go to Settings > Preferences > Files.  Select "Delete downloaded packages after installation".  Clicking "Delete Cached Package Files" will clear them all immediately.  If you run the above in the terminal again you should see the space free now.

Honestly I don't know why they're kept by default, they sit there and take up space and if they were needed again they could just be downloaded again.

---

### Post by trampintransit2 on 2010-01-06
That's the fella...thanks for that

---

