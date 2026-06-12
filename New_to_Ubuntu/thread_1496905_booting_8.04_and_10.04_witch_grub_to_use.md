---
title: "booting 8.04 and 10.04 witch grub to use"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by klein de usa on 2010-05-29
hi 
i have 8.04 installed on two computers i would like to also install 10.04 on the same computers. my question is if i install 10.04 and let grub 2 handle the boot for 10.04 and 8.04, when the kernel updates in 8.04 how do i update this in 10.04 grub2?  before when i had to do this i would just edit the grub menu list of the old style grub, after doing much reading i don't think it is that easy. would running update grub from 10.04 pick up the change in the 8.04 kernel?

---

### Post by confused57 on 2010-05-29
> **klein de usa said:**
> hi 
i have 8.04 installed on two computers i would like to also install 10.04 on the same computers. my question is if i install 10.04 and let grub 2 handle the boot for 10.04 and 8.04, when the kernel updates in 8.04 how do i update this in 10.04 grub2?  before when i had to do this i would just edit the grub menu list of the old style grub, after doing much reading i don't think it is that easy. would running update grub from 10.04 pick up the change in the 8.04 kernel?

I would recommend allowing 10.04 to install grub2 to your first boot drive's mbr, probably /dev/sda?  Then when Hardy has a kernel update, just boot into Lucid & run:
```
sudo update-grub
```

I'm much more familiar with legacy-grub, but I've found that it's easier to let 10.04 manage the booting of other OS.

---

