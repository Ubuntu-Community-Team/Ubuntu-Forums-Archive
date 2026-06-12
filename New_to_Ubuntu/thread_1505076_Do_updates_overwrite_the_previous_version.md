---
title: "Do updates overwrite the previous version?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-08
I was just notified about 100mb worth of updates in my update manager, realistically is it going to fill my hard drive up with another 100 mb?

---

### Post by linuxman94 on 2010-06-08
Your used space may increase a little, but when ubuntu updates packages, it removes the previous version so that only one version remains insatlled.

---

### Post by Paqman on 2010-06-08
If you want to know exactly how much extra space will be required for an update, do it through Synaptic. Just open it up, hit "Mark all upgrades" and "Apply". It'll tell you how big the download will be, and how much space it'll take up.

Generally speaking, updates do take a small amount of extra space, but nowhere near the size of the download. Some updates actually reduce the space used.

---

### Post by oldsoundguy on 2010-06-08
You can always install Ubuntu Tweak and use it to remove all of the stuff left behind .. and Ubuntu DOES leave stuff behind .. not anywhere NEAR the piles of garbage left in Windows, but there IS "stuff" left.

---

### Post by Legendary_Bibo on 2010-06-08
ah okay, because the way I was looking at it was it may be 100 mb, but if it's that much every few days then my hard drive will fill in a short amount of time.

---

### Post by Paqman on 2010-06-08
> **oldsoundguy said:**
> Ubuntu DOES leave stuff behind .. not anywhere NEAR the piles of garbage left in Windows, but there IS "stuff" left.

Not really, the only stuff left behind when a package is upgraded or uninstalled is the old debs in the apt cache.

---

### Post by doas777 on 2010-06-08
depends on the update. kernels are some of the weightiest updates (30+ MB) and they do not uninstall the previous version, so that you can boot into the old one if the new version doesn't work out. also be sure to run 'apt-get autoremove' to get rid of any dropped dependencies.

---

### Post by exodus_ on 2010-06-08
> **Paqman said:**
> Not really, the only stuff left behind when a package is upgraded or uninstalled is the old debs in the apt cache.

AFAIK there is also some configuration files and whatnot left around when removing a package.

---

### Post by Paqman on 2010-06-08
> **exodus_ said:**
> AFAIK there is also some configuration files and whatnot left around when removing a package.

If you do a normal uninstall, then settings are left in their .folder in your home (and possibly other stuff like gconf). But that's done deliberately, so that if you reinstall it sets up exactly how it was before. 

If you purge the package fully, then everything is removed.

---

### Post by doas777 on 2010-06-08
> **exodus_ said:**
> AFAIK there is also some configuration files and whatnot left around when removing a package.
config files are usually backed up and then upgraded in place, so you may still end up with backup files, and it seems like sometimes the dpkg seems to lose track of some config files in ~, but 'purge' does seem to get most of them. hey, whats a couple of bytes between freinds?

---

