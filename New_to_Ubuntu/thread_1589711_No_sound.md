---
title: "No sound"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by llamaboy on 2010-10-06
I keep losing my sound card. I am running Ubuntu 10.04 and have a hp dv2815nr laptop, which originally took the Conexant Smart High-Def driver 221 that hp installed on it. I did not originally have sound when I first installed and had looked around and found this code:

cd ~
mkdir src
cd src
mkdir alsa
cd alsa
wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)
tar -xvpf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure
sudo make
sudo make install-modules


which appeared to help. However, a couple days after having sound, I closed my laptop and it went to sleep (not for the first time during that duration of time, and when i "woke it up" i didn't have sound. I tried hte code again several times, between powering it off. I have searched hard to figure out what the problem is, please help.

---

### Post by Locke_99GS on 2010-10-07
I've noticed that sleep and hibernation can sometimes, somehow, screw up mixer settings. Go to *alsamixer* from a terminal and play with mutes and off volumes to see if you can get your sound back.

---

