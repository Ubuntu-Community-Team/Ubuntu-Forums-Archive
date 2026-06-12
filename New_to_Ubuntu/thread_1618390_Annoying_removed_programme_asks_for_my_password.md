---
title: "Annoying removed programme asks for my password"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Jetro on 2010-11-10
I installed Dexrex (an IM backup device), removed it (via Synaptic), but when starting Kubuntu (Ubuntu with a KDE session), Dexrex IM Backup asks for my password, and it says that it's in the folder /usr/bin/Dexrex. There's no such folder for me to delete, so this message pops up every time I login! Is there a way to completely remove the annoying and useless Dexrex?

It's weird that it starts up in my Kubuntu session, as I never have it running. At least, not as I can see.

---

### Post by TeoBigusGeekus on 2010-11-10
Check where kubuntu stores its startup apps and remove whatever remnant from dexrex there is.

---

### Post by Jetro on 2010-11-10
I'm sorry, where can I find that? I found that you could look in home/user/.kde/Autostart, but in that folder, there was nothing.

---

### Post by aysiu on 2010-11-10
This may be kind of old-school, but try ```
sudo updatedb
locate Dexrex
grep -inr Dexrex ~/
``` and see what pops up.

---

### Post by sisco311 on 2010-11-10
> **aysiu said:**
> This may be kind of old-school, but try ```
sudo updatedb
locate Dexrex
grep -inr Dexrex ~/
``` and see what pops up.

It's not old-school, it's a good idea.

But I would check first the autostart directories (~/.config/autostart/ and /etc/xdg/autostart/).

---

### Post by Jetro on 2010-11-11
> **sisco311 said:**
> But I would check first the autostart directories (~/.config/autostart/ and /etc/xdg/autostart/).
Nothing in the first one. Lots in the second, though. Is this what I have to do when I wish to remove startup apps? It seems a bit primitive.

aysiu: Your command revealed two locations, so now I can finally delete it. Thanks!

---

### Post by aysiu on 2010-11-11
> **Jetro said:**
> Is this what I have to do when I wish to remove startup apps? It seems a bit primitive. No, this isn't standard procedure. If you have time, you should probably file a bug report on this program's package, so the developers know removing the package does not remove the autostart entry.

---

### Post by Jetro on 2010-11-11
Yes, but I was more wondering how you select what programs that should run at startup. In GNOME, it's Startup Programs. I haven't found something similar in KDE yet.

---

### Post by aysiu on 2010-11-11
> **Jetro said:**
> Yes, but I was more wondering how you select what programs that should run at startup. In GNOME, it's Startup Programs. I haven't found something similar in KDE yet.
Apparently there is a program that can manage it:
[http://docs.kde.org/development/en/kdebase-workspace/kcontrol/autostart/index.html](http://docs.kde.org/development/en/kdebase-workspace/kcontrol/autostart/index.html)

Not sure if that's installed in Kubuntu by default or not.

---

