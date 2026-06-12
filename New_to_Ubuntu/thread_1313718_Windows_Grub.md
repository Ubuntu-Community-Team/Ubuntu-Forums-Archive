---
title: "Windows Grub"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-11-04
I wanted to install a new ubuntu over my old one, but a fresh one, so wipe the partition and install new, and just want to make sure that it's easy to set the windows load option in grub after? I've saved the menu.lst.

Thanks for considering,
HO

---

### Post by N4zgu1 on 2009-11-04
I don't understand what is your question but ubuntu detects windows automatically, however it is a good idea to backup menu.lst anyway

---

### Post by QIII on 2009-11-04
Do you intend to install Karmic?

Are you going to save your /home partition (or folder if it is currently set up that way)?

Karmic does not use GRUB, it uses GRUB2.  menu.lst is not used any longer in GRUB2.

But you can certainly detect other OSs and have GRUB2 give you the option to select them.

---

### Post by nhasian on 2009-11-04
when you install ubuntu 9.10 it will autodetect windows and add it to the bootloader.  there is a bug however that in some rare cases it fails to do so when you install next to windows.  its easy to correct though, from a terminal simply type:

```
sudo update-grub
```

its documented in the release notes.

---

### Post by hungryOrb on 2009-11-04
Thankyou fine gentlemen for the help, appreciate.

---

