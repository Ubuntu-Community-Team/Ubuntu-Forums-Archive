---
title: "Triple booting"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by misswham on 2010-02-17
I have dual boot xp first then ubuntu 8.04.  I would like to add Linux Mint and was wondering whats the easiest way to do it?

---

### Post by walt.smith1960 on 2010-02-18
but I use this: [http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm). Thing'll support over 200 primary partitions though I don't know why I'd want 10% of that number. Once installed you can determine which other partitions each O.S. can "see". The tricky part of using BootItNG to install Ubuntu is on the last screen of the install process you need to click the "advanced" buttton and put GRUB in the new partition, not in the MBR. Grub will override BootIt NG and Grub will only see the new partition I think. There's a recovery process but it's easier to do it right the first time.

---

