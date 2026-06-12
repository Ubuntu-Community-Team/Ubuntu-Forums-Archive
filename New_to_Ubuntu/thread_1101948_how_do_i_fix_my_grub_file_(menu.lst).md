---
title: "how do i fix my grub file (menu.lst)?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by andrewwg94 on 2009-03-20
i did sudo update-grub, and for some reason it deleted all my boot entries, so when i boot my computer, i get the grub command line:

grub>

how do i fix this? can i just boot from that command line? ubuntu is in (0,5)

thanks!

---

### Post by meierfra. on 2009-03-20
in the grub command line type:

```
root (hd0,5)

kernel /vmlinuz root=/dev/sda6  ro

initrd /initrd.img

boot
```


This should be you into Ubuntu.

---

