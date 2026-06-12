---
title: "how to reinstall"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by yungballla6 on 2011-04-25
I'm running ubuntu 11.04 beta 2 and I screwed around way to much with compiz and such and was wondering if I can just reinstall it? Or when the final release comes out the 28th will I be able to install that version fresh? Thank you in advance

---

### Post by wolfen69 on 2011-04-25
Sure, you can install whatever you want. There are no limitations on reinstalling.

---

### Post by K_45 on 2011-04-25
You can reinstall the vast majority versions of Linux distro's as many times as you want on whatever you want. You can also create your own distro, but that is another thread.

---

### Post by 3rdalbum on 2011-04-25
> **yungballla6 said:**
> I'm running ubuntu 11.04 beta 2 and I screwed around way to much with compiz and such and was wondering if I can just reinstall it?

Compiz settings are in the home directory. If you reinstall Compiz, you'll still be using the exact same settings. If you reinstall Ubuntu with the option to preserve your home directory, then you'll still be using those bad settings.

Better off removing all the Compiz-related settings from gconf-editor, which will take Compiz back to its defaults.

If you really want to, you could reinstall the whole Ubuntu; but make sure the Compiz settings are gone too (i.e. erase the disk/partition).

---

