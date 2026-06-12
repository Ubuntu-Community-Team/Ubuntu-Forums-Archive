---
title: "Booting to Command Prompt"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by stuart264 on 2010-01-19
I made a mistake yesterday, I was trying to edit my X server config file to run with openchrome drivers when my pc was plugged into the VGA port on my Toshiba HD TV.

Only problem is it didnt work and now I cant get into the command prompt to undo the changes as the display continually flickers and wont show anything, I have tried Ctrl + Alt F1-F6 with no success, can anyone tell me how I need to alter my Grub boot settings so I boot into a command prompt rather than the Gnome desktop to fix the driver problem?

Stuart

---

### Post by inobe on 2010-01-19
have you tried recovery mode ?


restart and hit escape when you see the grub countdown, choose recovery mode, you can than select root shell.

---

### Post by stuart264 on 2010-01-19
yup, same problem, I need to boot into a basic command prompt by editing the grub boot lines as thats the only bit I can get into

---

### Post by inobe on 2010-01-19
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

i hope that helps

---

### Post by stuart264 on 2010-01-20
Didnt I am afraid, if I booted from a live CD would I be able to edit the file on the hard drive that way to correct the error?

---

### Post by nothingspecial on 2010-01-20
Yep.

---

### Post by anaconda on 2010-01-20
> **stuart264 said:**
> Didnt I am afraid, if I booted from a live CD would I be able to edit the file on the hard drive that way to correct the error?

Yes, you can edit the file if you boot from CD.

What version of ubuntu have you got?

The new versions 9.04 and 9.10 should work even if you delete the whole file (or rather just change the filename.)

---

### Post by caravel on 2010-01-20
Ctrl + Alt + F1-F6 should be working, if it's not then the problem is not xorg.conf but the kernel module for the display.

You should also be able to boot to just a root shell from the grub boot menu by selecting "recovery mode".

Have you tried booting an older kernel in recovery mode?

---

