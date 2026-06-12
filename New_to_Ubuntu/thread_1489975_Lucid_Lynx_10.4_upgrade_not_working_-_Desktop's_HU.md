---
title: "Lucid Lynx 10.4 upgrade not working - Desktop's HUGE"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by coopelectric on 2010-05-21
EVERYTHING IS HUGE/WEIRD/Incomplete! I upgraded Ubuntu from 9.10 Karmic Koala to Lucid Lynx 10.4 through the Update Manager and when I restarted my computer the desktop (or GUI) was all messed up. The panel, desktop, fonts, icons (GUI) are huge gigantic big like a magnifying glass is on them and they don't work or link to the right apps or programs - they aren't what they say they are. I have an NVIDIA card, btw. "Applications", for instance, is divided into three links (when I hold the over-sized cursor over it) that include: "Help", OpenOffice", "Skype", "Transmission", "qBittorrent" and so on. Everything is huge, weird, disjointed and only shows about 30% of what should be available on the desktop/panel. This is extremely disappointing. Why would something this horrible be released as "noob-friendly" by making it an inviting "Click here!" option in Update Manager? There's not an easy "undo changes" or "reinstall Lynx" option in Update Manager either. I did back up 9.10 as it suggested, but the GRUB only lists 10.4 versions for recovery mode, etc. It also takes much much much longer to load (I thought it was hanging) and flashes a bunch of crazy crap on the splash screen before the "loading" screen. Thanks in advance for any help....

Now I will list key phrases to lead others here: Ubuntu Hardy Heron 9.10 upgrade update Lucid Lynx 10.4 10.4LTS GUI all messed up, doesn't work, sucks, how do I reinstall go back to 9.10 without losing my files, info, data, settings, packages,

---

### Post by -humanaut- on 2010-05-21
Sounds to me like an incomplete upgrade it's fixable but i'd highly recommend a clean install at this point unless you have a fairly good working knowledge of Linux.

---

### Post by wojox on 2010-05-21
Have you gone into Hardware Drivers to see if your nvidia driver is activated?

---

### Post by jebuntu on 2010-05-21
I'm in pretty much the same boat after an upgrade from 9.10. Nvidia card ... obvious video problems. System hangs with an error msg about Nvidia drivers and at that point I don't have keyboard, mouse etc.

1) Is it possible to recover from here ... very little penguin experience. I've got the 10.04 alternate CD.

2) If i do a new install will i loose everything? I installed 9.x with multiple partitions but enough time has passed that I recall little of how I set it up and Partition Magic doesn't show any sort of labels on them (ext3). No backup but would like to keep SeaMonkey and a few other things if possible.

Feedback please ... jim

---

### Post by -humanaut- on 2010-05-21
> **jebuntu said:**
> I'm in pretty much the same boat after an upgrade from 9.10. Nvidia card ... obvious video problems. System hangs with an error msg about Nvidia drivers and at that point I don't have keyboard, mouse etc.

1) Is it possible to recover from here ... very little penguin experience. I've got the 10.04 alternate CD.

2) If i do a new install will i loose everything? I installed 9.x with multiple partitions but enough time has passed that I recall little of how I set it up and Partition Magic doesn't show any sort of labels on them (ext3). No backup but would like to keep SeaMonkey and a few other things if possible.

Feedback please ... jim

As long as you kept a separate /(root) and /home partition you should be able to save all your data with a fresh install.

---

### Post by Frogs Hair on 2010-05-21
If you were using the Nvidia 185 driver in 9.10  you need to install the 173 or 195.36 for 10.04.

---

### Post by coopelectric on 2010-05-21
> **wojox said:**
> Have you gone into Hardware Drivers to see if your nvidia driver is activated?


Can I get there from the terminal? I can't get to "Applications", "Places" or "System" because the desktop is wrecked but I can get to the terminal through Alt+F2.

---

### Post by wojox on 2010-05-22
> **coopelectric said:**
> Can I get there from the terminal? I can't get to "Applications", "Places" or "System" because the desktop is wrecked but I can get to the terminal through Alt+F2.

Try Alt+F2 and enter 

```
gnome-control-center
```

---

### Post by jebuntu on 2010-05-22
> **-humanaut- said:**
> As long as you kept a separate /(root) and /home partition you should be able to save all your data with a fresh install.

Which I did (and a couple more /usr? ) BUT I didn't document (rather can't find it a couple years later) which partitions were which and the partition manager on the alternate CD doesn't recognize them with any sorts of labels. Would there be a faq / howto about how to proceed? (Note ... a jpg of my partitions is attached.)(and I'm using the earlier GRUB to dual boot XP and Ubuntu)

---

### Post by coopelectric on 2010-05-23
> **Frogs Hair said:**
> If you were using the Nvidia 185 driver in 9.10  you need to install the 173 or 195.36 for 10.04.

Okay, I stumbled around and did this. Everything looks normal now, so I can access everything again. The reboot time is still unbelievably slow though, so I think that I'm still missing/have corrupted packages from the upgrade. Now at least I have functionality though. I'm going to back everything up and do a fresh install. THANKS EVERYONE! BTW, how do I file this under "SOLVED" and how on earth do you people figure this stuff out? I'd be screwed if I didn't have an Internet connection. How do you expect Ubuntu to be the post-apocalyptic OS of choice if it's all online communiques?? :P

---

