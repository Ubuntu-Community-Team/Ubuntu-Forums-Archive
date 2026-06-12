---
title: "Sound went on 6th Feb having worked before then!"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by muncy on 2010-02-07
I lost sound in 9.10 yesterday. When I first installed 9.10 I had no sound so followed some instructions I found to upgrade Asla to 1.0.21. After this it worked fine until yesterday. I believe that one of two things can have caused this.

1. I installed a Huwaii modem on the windows partition of my computer. (Unlikelt to have been the cause but I've uninstalled it just in case)
2. I accepted the updates that Update Manager wanted to install.

I had also used the Huwaii modem on the Ubuntu side a few days earlier but I'm pretty sure that I continued to have sound until yesterday.

I have removed, reinstalled re-upgraded Alsa and followed the advice in this thread [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but still no go. In pulse I can see the bar flickering to indicate input and my system seems to recognise that I have a hda-intel sound card

---

### Post by muncy on 2010-02-07
Seems that yesterdays upgrade overwrote /etc/modprobe.d/alsa-base.conf: 

To fix the problem I had to add these lines.

  options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

---

