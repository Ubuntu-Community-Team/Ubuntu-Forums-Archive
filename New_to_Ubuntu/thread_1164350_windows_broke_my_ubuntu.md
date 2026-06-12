---
title: "windows broke my ubuntu"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by schoolboy666 on 2009-05-19
hey,

i wanted to install windows 2000 for music production on my laptop next to my ubuntu,
but when i installed windows cmpletely ignored the grub menu so i tried this:

> code:
       
       sudo grub
       find /boot/grub/sage1`
       root (hd0,6)
       setup (hd0,6)
       quit

after that my windows wouldn't startup
and my ubuntu still did'nt start.

i have a data partition and i don't want to loose the files that are on it, and i dont want to loose my ubuntu installation either.

is there someway to restore ubuntu and get rid of windows withuot loosing the old installation of ubuntu and all the settings i made?

hope someone can help,

---

### Post by waspbr on 2009-05-19
windows will always write its own MBR and ignore any other OS. 

I would suggest you download and burn a  supergrub disk [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") , just pop it in at boot and follow the instructions, everything should be sorted out then

---

