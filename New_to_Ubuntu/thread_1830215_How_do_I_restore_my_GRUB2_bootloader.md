---
title: "How do I restore my GRUB2 bootloader?"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by skoomafiend on 2011-08-21
Hi!

I installed the "xfce4" package to try out the simpler interface. I decided I'd like to go back to Unity for now, but I'm apprehensive about uninstalling the xfce4 package because of the bootloader change! If I uninstall xfce, will my GRUB2 bootloader be restored? Or will my PC just boot to nothing? If that's the case, how do I get around this!?

:confused:

---

### Post by sanderd17 on 2011-08-21
To use unity, you just need to select "Ubuntu" as your desktop environment when you log in (the point where you have to give your pwd).

---

### Post by skoomafiend on 2011-08-21
Thank you! I'd like to uninstall the xfce4 package however just to free up space. Even though I've switched back to Unity, the bootloader is still hasn't changed (it's the one that got installed alongside xfce4). If I uninstall xfce4, will my GRUB2 bootloader automatically restore?

---

### Post by sanderd17 on 2011-08-21
The DE has nothing to do with the bootloader, so GRUB does not need to be restored.

---

### Post by coffeecat on 2011-08-21
> **skoomafiend said:**
> Even though I've switched back to Unity, the bootloader is still hasn't changed (it's the one that got installed alongside xfce4).

Why do you believe that installing the xfce4 package installed a bootloader?

**EDIT**: by the way the xfce4 package is only a metapackage and removing it will free just a few kilobytes of space. If you wish to clean out all the xfce stuff, but retain gnome and Unity, have a look here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

However, that is for getting back to a pure gnome after installing the xubuntu-desktop metapackage and dependencies, not the xfce4 metapackage and dependencies. There may be some detailed differences.

---

