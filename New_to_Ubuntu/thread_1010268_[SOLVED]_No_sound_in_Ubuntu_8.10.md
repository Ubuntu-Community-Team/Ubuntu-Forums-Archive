---
title: "[SOLVED] No sound in Ubuntu 8.10"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Gow524 on 2008-12-13
Hi,

I am new to Ubuntu and I need some help with audio.  I downloaded an ISO image of Ubuntu 8.10, burn it to cd, and installed in a single hard drive. Windows XP professional is installed in a separate hard drive.  I have no audio coming out of the speakers.  I have look at alsamixer, but audio is no muted. I have an Audigy 2 sound card that works just fine under WinXP professional.

---

### Post by Elfy on 2008-12-13
Double click the vol icon - there should be a switches tab - it'll have a digital/analog switch - disable it.

---

### Post by gettinoriginal on 2008-12-13
You should also install pulse audio from synaptic.  Also check under System > Preference > Sound and set devices as autodetect

---

### Post by sneeks on 2008-12-13
also in the synaptic package manager,there is an prog there for old soundcards like yours,if you search for alsa firmwae it should solve your problem if un-ticking digital sound dont.

---

### Post by Gow524 on 2008-12-13
Right on! it works.  the volume icon did the trick. (the tab knows as "Switches" was the culprit). Thanks for the aw some support.

---

