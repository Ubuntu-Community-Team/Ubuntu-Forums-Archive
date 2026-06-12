---
title: "not sure what i did wrong"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by rwltrz4 on 2009-12-30
partitioned my mac for dual boot with karmic, installed refit, installed karmic and now at boot i have 2 options osx or ubuntu however its not saying ubuntu it says legacy and when i boot it does nothing


i formatted partition for ubuntu as ext3 boot from / and also did a swap

---

### Post by thelethargarian on 2009-12-30
It may have just been a mistake in the grub configuration, which you could fix by booting it up with a live CD and changing it. Otherwise, you can just reinstall.

---

### Post by rwltrz4 on 2009-12-30
actually after a search i found this


make sure you click the "Advanced" button. "Install boot loader" should be checked. The idea is to install the boot loader on the partition that your Ubuntu installation is on. On my machine, it's /dev/sda3 (sda1 is the EFI partition, sda2 is the OS X partition, sda3 is the Ubuntu partition, and sda4 is the Linux swap partition)"


guess what , i did not touch advanced button so now my question is

what can i do now? do i have to reinstall?

---

### Post by rwltrz4 on 2009-12-30
> **thelethargarian said:**
> It may have just been a mistake in the grub configuration, which you could fix by booting it up with a live CD and changing it. Otherwise, you can just reinstall.

so if i run live cd, what steps do i take?

---

### Post by thelethargarian on 2009-12-30
Oh, I missed the part that says you used rEFIt. I know nothing about using that, and therefore can't help you there. Sorry...

---

