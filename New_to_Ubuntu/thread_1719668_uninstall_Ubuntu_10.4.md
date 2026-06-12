---
title: "uninstall Ubuntu 10.4"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by jagandecapri on 2011-04-02
I was dual booting my laptop with Windows 7 and Ubuntu 10.4. then I installed Ubuntu 10.10 by creating another partition. Can i delete the Ubuntu 10.4 partition from Ubuntu's disk utility without effecting grub boot loader?

---

### Post by Rubi1200 on 2011-04-02
> **jagandecapri said:**
> I was dual booting my laptop with Windows 7 and Ubuntu 10.4. then I installed Ubuntu 10.10 by creating another partition. Can i delete the Ubuntu 10.4 partition from Ubuntu's disk utility without effecting grub boot loader?

> Can i delete the Ubuntu 10.4 partition from Ubuntu's disk utility without effecting grub boot loader?
It depends. If you installed 10.10 after 10.04 and it now controls booting, then probably yes.

Even if something goes wrong, reinstalling GRUB from the LiveCD is a matter of 2 commands and then 1 more in Ubuntu afterwards.

I also suggest you use GParted on the LiveCD to do this so the partitions are unmounted. You may need to turn the swap partition off; right-click Swapoff.

Above all, make backups first BEFORE playing around with partitions; you never know when soomething might go wrong.

---

### Post by jagandecapri on 2011-04-02
thx for the info....ya it did effect the boot....in fact the whole GRUB did not work but I manage to restore it using the Live CD....TQ

---

### Post by Rubi1200 on 2011-04-02
No problem, you are more than welcome :-)

Glad you got it sorted out.

---

