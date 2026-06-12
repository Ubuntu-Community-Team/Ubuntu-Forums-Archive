---
title: "New edit with a fail."
date: 2011-01-27
forum: New to Ubuntu
---

### Post by rtindall on 2011-01-27
Earlier I attempted to boot into the equivalent of windows command prompt safe mode on Ubuntu 9.10 Server so I could unmount and use Ghost Image on the hard drive to make a image of it. I couldn't figure out how to get into just the terminal of it without it logging into a user profile so after some reading I discovered if I changed a key in etc/default/grub under GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" and then update the grub I could get this command worthy equivalant. However after getting that I learned how to unmount the disk drive and now nothing really works on it. I can't exit this text based command line and I can't load the grub to give me a GUI that I can logon with. I'm pretty confused at this point so any help would be appreciated. Thanks!:lolflag:

---

### Post by rtindall on 2011-01-27
Also if there were to be just a way to roll it back to about 2 days ago that would suffice. Once again any help is greatly appreciated!

---

### Post by uRock on 2011-01-27
Ubuntu Server doesn't come with a GUI. ```
sudo apt-get install ubuntu-desktop
``` will install the GUI.

---

### Post by TeoBigusGeekus on 2011-01-27
Assuming you are on command line
```
sudo nano /etc/default/grub
```
Make the necessary changes, Ctrl+X to exit (don't forget to save),
```
sudo update-grub
```
and finally
```
sudo reboot
```

---

### Post by rtindall on 2011-01-27
Thanks guys! This seems to have fixed my problem. Don't be worried though I'm sure I'll be back soon with more things I've messed up :lolflag::lolflag:

---

