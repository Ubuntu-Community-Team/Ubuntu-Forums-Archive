---
title: "Clonezilla (stable) not restoring grub2 for karmic"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-11-18
Hi,

I completely trashed my karmic/crunchbang dualboot-(same drive) system the other day, and I tried to restore my backup twice but it failed. Both times Clonezilla reported the grub couldn't be installed. As far as I know, as of now, grub2 can't be restored easily via live cd yet...  I am using clonezilla-live-1.2.2.-31.iso (the stable version) and have tried to restore from an img backup from my storage drive. 

I had a backup of jaunty and I was able to restore without problem, a few times. I deleted my karmic backup already thinking it was probably corrupted, but then I started thinking that maybe I should have tried using the alternate version (karmic based) clonezilla since I am working with grub2.

So can anybody advise me if I should be using the alternative version clonezilla (based on Karmic) if I'm working with karmic (gdm2) based backups?

Edit, I found a grub2 reinstallation method, see post below.

Thanks,
James

---

### Post by ankspo71 on 2009-11-18
I have found a grub2 repair method. More complicated than restoring grub1 though.
[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by kaibob on 2009-11-20
> **ankspo71 said:**
> I had a backup of jaunty and I was able to restore without problem, a few times. I deleted my karmic backup already thinking it was probably corrupted, but then I started thinking that maybe I should have tried using the alternate version (karmic based) clonezilla since I am working with grub2.

I couldn't get clonezilla_live_stable to backup my karmic install. I believe this was because my file system was ext4. I began using the karmic-based Clonezilla and have not had any issues with creating or restoring the images, and grub2 works fine after restore. So, based on my experience, I would recommend that you use the karmic-based version.

---

### Post by ankspo71 on 2009-11-20
Thanks Kaibob,
It's reassuring to know that Clonezilla will work with Karmic. I'll get the alternate version and try a test backup and restore of a default karmic install, that way I'll know right away if can depend on it or not.
James

---

