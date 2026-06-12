---
title: "No desktop icons"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by TIGGER959 on 2009-09-30
I installed Ubuntu on a PC that I need to move all the personal files from before I re-install the operating system.  Although I can see the drive id in the Places Folder, I cannot see it on my desktop.  Nor can I see the flash drive I inserted.  I click on the name (263.4 gb drive media in this case) and the arrow spins and returns to an arrow without adding the media to the desktop.

Any suggestions or help would be deeply appreciated.  Being an absolute novice, can I just move files from one drive to the other by dragging?

Thanks!

---

### Post by arrange on 2009-09-30
> **TIGGER959 said:**
>  I click on the name (263.4 gb drive media in this case) and the arrow spins and returns to an arrow without adding the media to the desktop.

Any suggestions or help would be deeply appreciated.  Being an absolute novice, can I just move files from one drive to the other by dragging?
ad 1) Can you please click on the drive again, wait for the arrow to stop spinning, and then post the output of ```
dmesg | tail
sudo fdisk -l
```from the Terminal? What kind of drive is it?

ad 2) Generally speaking, yes.

---

