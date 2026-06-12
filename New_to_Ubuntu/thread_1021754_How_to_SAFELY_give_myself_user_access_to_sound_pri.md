---
title: "How to *SAFELY* give myself user access to sound priveledges?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by abben on 2008-12-25
Hey all. Here is what I know

- After install, I saw that xubuntu didn't load any drivers for my sound card, so I manually specified my sound blaster 16 drivers
- It now knows my sound card is there (hooray!), I get the startup drums at the login screen, etc. etc.
- I still don't get sound when playing a media file unless I use "sudo" when I launch the program.

I've been told that I need to give myself user level access to the sound. I don't understand how to do this in xubuntu 8.10. (I've followed some shady advice last time around, to disastrous results, hence the fresh install). I suspect there is an obvious, "real" way one is supposed to do this. What is it?

---

### Post by abn91c on 2008-12-25
this will make sure the sound card start at every boot
sudo alsactl store 0
for the root access go to the user settings>privileges and check all the boxes including sound also add yourself to the sound group

---

