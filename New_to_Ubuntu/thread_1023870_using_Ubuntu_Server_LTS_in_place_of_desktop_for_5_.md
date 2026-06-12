---
title: "using Ubuntu Server LTS in place of desktop for 5 years of support?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-28
Hello,

quick question. thread title pretty much sums it up.

if i want 5 years of support instead of 3, is there any reason not to go ahead and install server edition?

anything in Ubuntu desktop that _isnt _in Server?

any reason i cant uninstall Apache, MySQL, Perl, and whatever other packages define it as the "server" edition?

---

### Post by northern lights on 2008-12-28
> **earthpigg said:**
> any reason i cant uninstall Apache, MySQL, Perl, and whatever other packages define it as the "server" edition?
Theoretically, you could uninstall LAMP (which includes apache and the like).

> **earthpigg said:**
> anything in Ubuntu desktop that _isnt _in Server?You have to manually add the meta-package *ubuntu-desktop* for a GUI. But that's as easy as```
sudo apt-get install ubuntu-desktop
```

> **earthpigg said:**
> if i want 5 years of support instead of 3, is there any reason not to go ahead and install server edition?
However, your reason for wanting the Server Edition makes no sense to me whatsoever. And I think you'll experience the same soon and come to agree with me.

The desktop editions of non-LTS releases have a lifetime of 18 months (Feisty's just ended). I've never kept a release that long without either a fresh install or a distribution upgrade.

If you had the time, for shits and giggles, install Feisty and check out the difference to Intrepid or Hardy. Feisty could not write to ntfs without adding ntfs-3g from source, for instance...

---

### Post by igknighted on 2008-12-28
The media which you install with doesn't make any difference, it is how long the specific packages will be maintained.  The desktop software will stop getting security updates after 3 years regardless of which disk you used, whereas apache, mysql, etc. will all get updates for 5 years.

---

### Post by earthpigg on 2008-12-28
no security updates... but could i still install software from the repos?

---

