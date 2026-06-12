---
title: "7-zip"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-12
I installed minimal ubuntu on this old pc.One of the things I installed is p7-zip (full) and unrar (nonfree).Unlike on my main pc,richtclicking a zip file doesn't show the option to unpack.What do I need to install in order to get the job done?

---

### Post by Unlimited Bit on 2010-01-12
What file manager are you using ?

---

### Post by dzon65 on 2010-01-12
For now thunar,since I started this minimal using xfce4 but switched to gnome.

---

### Post by sisco311 on 2010-01-12
thunar-archive-plugin and xarchiver, squeeze, file-roller or ark

EDIT: 
thunar-archive-plugin recommends squeeze by default.

If you want to use ark, xarchiver or file-roller, then run something like: 
```
sudo apt-get --no-install-recommends install thunar-archive-plugin ark
```

---

### Post by dzon65 on 2010-01-12
Nope,no go.Open with xarchiver opens the window for a split second and disappears.

---

### Post by sisco311 on 2010-01-12
> **dzon65 said:**
> Nope,no go.Open with xarchiver opens the window for a split second and disappears.

Did you restart thunar?

---

### Post by dzon65 on 2010-01-12
Yep,quickly rebooted even,same result.

---

### Post by dzon65 on 2010-01-12
Maybe due to the very low specs of this old rig (128mb ram).Gonna "boost" it a little adding 512 (waaw).If it still doesn't wwork,perhaps nautilus.

---

### Post by jamesbannon on 2010-01-12
> **dzon65 said:**
> Nope,no go.Open with xarchiver opens the window for a split second and disappears.

Have you tried it from the command line? Sounds like you're missing a dependency or have the wrong version of a library.

---

### Post by dzon65 on 2010-01-12
Not from the command line.But,why should that make a difference?

---

### Post by jamesbannon on 2010-01-12
> **dzon65 said:**
> Not from the command line.But,why should that make a difference?

Because if xarchiver bombs, it should tell you why.

ETA: I meant to say, launch xarchiver from the command line rather than from a menu.

---

### Post by dzon65 on 2010-01-12
like I said,started this minimal using xfce4 and thunar.Since I didn't like the look of it,decided to go for a minimal gnome (gnome-core,gnome-theme....) it installed nautilus.Could this be conflicting?Ok,just read your last answer.Could you give me the command to use?

---

### Post by dzon65 on 2010-01-12
Removed thunar,tried nautilus.....same thing.Can't find  it,I'll consider the thread solved for now.

---

