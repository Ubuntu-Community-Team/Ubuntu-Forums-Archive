---
title: "Trying to install from hard disk"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by plarq on 2008-12-28
According to a tutorial that tells me to install linux without burning a disk, I setup my GRUB, put the files (including /.disk)of LIVE CD is in dev/sda5, have an empty ext3 format dev/sda6. Then I boot from the partition. grub.cfg like this:

{linux (hd0,6)/casper/vmlinuz boot=casper
 initrd (hd0,6)/casper/initrd.gz
}
Now the system load into a LIVE CD-like Live session. But when I try to install linux running Install from desktop, it gives me no partition to install.--I used my old Ubuntu Live CD to boot from CD-ROM, its installer gives me right partitions to install.

I don't know where I did wrong.

---

### Post by zvacet on 2008-12-28
I don´t know about that one but you can try [this.]("http://ubuntuforums.org/showthread.php?t=666267&highlight=iso+install")You will need one partition ~1GB and second larger on whitch you will install.

---

### Post by hyper_ch on 2008-12-28
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by billgoldberg on 2008-12-28
Try using the tool "unetbootin".

It doesn't get easier than that.

---

