---
title: "Help! Docky just stopped working."
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-03-16
Hello all,
Docky was working fine until about 2 hours ago. I restarted my computer and all of a sudden, it didn't work. It didn't launch on startup, I can't open it by going to Accessories>Docky, I can't create a shortcut and open it that way... nothing.

I tried uninstalling it and reinstalling it but that didn't work either.

The weird thing is... it works if I switch users. However, under my user account, it will not open. Please help!

---

### Post by ~Plue on 2011-03-16
> **Ranger_Joe said:**
> 
The weird thing is... it works if I switch users. However, under my user account, it will not open. Please help!
try removing your docky config files
it would be in your .config, .gconf or .local/share  folder (cant recall the exact one)

---

### Post by Ranger_Joe on 2011-03-16
I have no idea where to find any of that. Would that explain why it works for other users on my machine?

---

### Post by Ranger_Joe on 2011-03-16
If this helps AT ALL... I think it was totally accidental. I think some box somewhere accidentally got checked or something like that. I just don't understand why it has stopped working on my user profile.

---

### Post by ~Plue on 2011-03-17
> **Ranger_Joe said:**
> I have no idea where to find any of that.  Would that explain why it works for other users on my machine?
disregard that last comment. the config files *are* in .local/share .cache/docky and .gconf/apps/. (from the docky wiki) 
open your home directory and press ctrl+H to see hidden directories 

or just run the following 
```

rm -r ~/.local/share/docky     (if version 2.0.x)
rm -r ~/.local/share/dockmanager/         (if version 2.1.x)
rm -r ~/.cache/docky
gconftool-2 --recursive-unset /apps/docky-2

```> 
Would that explain why it works for other users on my machine?yep. each user's configuration is stored within their home folder

---

