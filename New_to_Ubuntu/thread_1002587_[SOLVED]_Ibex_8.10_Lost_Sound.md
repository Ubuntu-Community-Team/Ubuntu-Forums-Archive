---
title: "[SOLVED] Ibex 8.10 Lost Sound"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by MrWES on 2008-12-05
I installed GNOME sound mixer and now I have no sound at all, CD, DVD, etc. When open the mixer this is the error I'm getting:

Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names

Preferences | Sound is set to autodetect, I didn't change anything from the original install..and I had sound at one point.

Bill

---

### Post by zzHanks on 2008-12-05
Try this:
```
sudo apt-get install ubuntu-sounds
```

---

### Post by MrWES on 2008-12-05
> **zzHanks said:**
> Try this:
```
sudo apt-get install ubuntu-sounds
```

That wasn't it, newest version already installed. I have absolutely no sound, cd, dvd, rhythmbox, youtube, etc. etc. and I did at one point.

Any suggestions?

Bill

---

### Post by Hyper Tails on 2008-12-05
You can try this if it helps
fire up terminal and type the following commands (without the dollar signs)
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo init 6
sudo apt-get install alsa-base alsa-utils fast-user-switch-applet gdm gdm-themes kubuntu-kde4-desktop linux-sound-base
sudo init 6
```

or 

```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by MrWES on 2008-12-05
Sigh... I fixed it -- I noticed a lot of the volumes in the gnome alsa mixer were turn all the way down...Frig if I know how they got that way, but once I adjusted them I had sound. Lame.

Thanks for the effort,

Bill

---

