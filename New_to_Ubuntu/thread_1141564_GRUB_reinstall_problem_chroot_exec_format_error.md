---
title: "GRUB reinstall problem/ chroot exec format error"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by supererki on 2009-04-28
Hello.
so i messed up GRUB again, but i was not able to recover it this time. i booted from live cd 8.04, tried to reinstall grub but it said cannot mount your partition, couldnt find stage1 etcetc... so i mounted my root partition to /mount/root and i mounted proc to that folder and -o bind /dev etc . and then i did chroot /mount/root /bin/bash it said something like :
cannot execute /bin/bash: Exec format error ...
what can i do ?
i have 64bit machine but installer is for 32bit. may this be problem ? should i try with newer installer like 9.04?
anybody?
thanks
erki

---

### Post by supererki on 2009-04-28
anybody?

---

### Post by supererki on 2009-04-28
please. i have no clues myself for the moment

---

### Post by seanlano on 2010-05-03
It's a bit late now, but I am trying the same thing. It must some problem with the 32/64bit incompatibility. I'll have to use a 64bit LiveCD.

---

### Post by bumanie on 2010-05-03
Have you got grub-legacy or grub2 running? The reinstall is different between the two versions.

---

### Post by seanlano on 2010-05-03
Grub2. It's all working fine now though - I didn't even need to chroot. I found a tutorial that showed me how to reinstall Grub2 without chroot. I did this from a 64bit LiveCD though, so I can't vouch for whether this is architecture independent.

---

### Post by Curtos on 2010-12-28
> **seanlano said:**
> Grub2. It's all working fine now though - I didn't even need to chroot. I found a tutorial that showed me how to reinstall Grub2 without chroot. I did this from a 64bit LiveCD though, so I can't vouch for whether this is architecture independent.

Sorry to revive an old thread, but would you care to share what that method might be (the non chroot option)? 

Thanks!

---

