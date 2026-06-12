---
title: "[SOLVED] have updated and lost sound"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by kriket on 2008-12-21
I have just bought a new Toshiba NB100 Note Book, which comes with Ubuntu pre-installed.

Sound was working fine, then I installed the updates now I have no sound.

I have the speaker icon, with a sort round circular sign on it. When I double click on it, I get the following message; No volume control GStreamer plugins and/or devices found.

Please can some one help.

---

### Post by kriket on 2008-12-21
I found the answer!!!!

sudo mv /lib/modules/2.6.24-19-lpia/updates/sound ~/sound
sudo depmod -a

This worked for me, I hope it helps others.

---

