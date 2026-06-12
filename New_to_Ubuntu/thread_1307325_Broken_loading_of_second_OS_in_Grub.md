---
title: "Broken loading of second OS in Grub"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by scarletbanner on 2009-10-31
I had Ubuntu 9.04 and Windows XP Media Center edition running fine together... As 9.10 was released I decided to do a fresh install of Ubuntu. Deleted the Ubuntu partition, installed 9.10.

Ubuntu works fine, but when attempting to load Windows through Grub gets essentially a blank screen, with a blinking underscore.
I do not believe it's a problem with the partition itself, I can access it just fine through Ubuntu after I mount it.

GParted shows it's mount point weird though.
```

Partition                File system           Mount point
/dev/sda1                NTFS                 /media/PRESARIO
```They are both on the same drive... in /boot/grub/menu.lst, Windows is not listed.
Is there anything I can do in specific to remedy this problem?

---

### Post by humphreybc on 2009-10-31
Sounds like a problem with grub2 not recognizing another OS.

Try running this in Karmic:

```

sudo update-grub

```

See if that makes any difference. Hopefully it picks up the XP install automagically :)

---

### Post by scarletbanner on 2009-10-31
It picked it up in the terminal, however upon restarting Grub no longer loads at all; it attempts to load XP directly now, which still doesn't work.

Alright, deleted the Linux partition and reinstalled it. At least that works at the moment again.

Also, my problem isn't so much of it not being picked up so much as the actual loading of XP has been broken.

---

