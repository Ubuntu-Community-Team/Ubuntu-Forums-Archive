---
title: "Partition Help and Grub Problem"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by miruchi_dave on 2009-05-20
):P Hello Ubuntu users. I am relatively new to Ubuntu, as I am a Windows user by default. That said I would like to install XP alongside Ubuntu so I can use either as I see fit. Before I installed Ubuntu, my computer's 160gb harddrive was partitioned into two 80gb halves but I'm not sure if it's still partitioned, Ubuntu guided me through it so I didn't set it up. I had Windows installed previously but it had to be uninstalled because it wouldn't accept my key or whatever, I have a working copy now but I would like to install both. I was wondering if there was a fail-safe method I could use to install Windows XP so that I can choose it from GRUB.

Also, when I updated Ubuntu after I installed it, and it no longer works, I have to select an alternate from GRUB (if it helps I can post the options). Does anyone know what caused this problem and if I can fix it? Or at least make it default to the working one would be fine.

---

### Post by GMachine_24 on 2009-05-20
Hi:

I'm not sure what problem(s) you are having. Normally, when you install Ubuntu onto a system that already has Windows, you install Ubuntu onto separate partitions that are formatted and created during your install. I'm sure you know this. Anyway, GRUB typically is configured so, when you boot your computer after your Ubuntu install, you can select to boot from Ubuntu or Windows. There is a file that tells the computer what options you have when booting your computer and you can edit this file if you need to.

However, as I mentioned, I'm unclear as to exactly what happens after you install Ubuntu.

It might be a good idea to boot Ubuntu "live", meaning your computer will boot from the CD and not install on your hard drive. This way, once you have booted into Live Ubuntu, you can run the "gparted" program and see how your hard drive is partitioned and formatted. Gparted will display your partitions and tell you if they are NTFS, ext3 or ext4 (Linux partitions), etc.

Give us the details here.

If you are at the point where you are wanting to reinstall Windows and Ubuntu, make that clear. Also, if you want to keep your hard drive divided into two separate sections, let us know that.

As a general rule more information is better. :)

---

### Post by presence1960 on 2009-05-20
in Ubuntu open a terminal- Applications > Accessories > Terminal. Run this command : ```
sudo fdisk -l
``` BTW that is a lowercase L. This will provide info about your disks and partitions. Paste the output here please so we can see exactly what you have.

---

