---
title: "Will an ext3 booloader continue to be OK for ext 4FS's"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by mikodo on 2010-01-09
I already have an ext3 bootloader booting for Hardy and Karmic. I will be getting rid of the Hardy partition soon to make room for Lucid. I don't use Hardy much anymore. Gparted screenshot below.

Question:

Will it always be OK to boot from an ext3 bootloader in future ext4 FS's or will I eventually have to change it to ext4 also?

Thankyou.

---

### Post by warfacegod on 2010-01-09
You shouldn't have to change it for years. Blurry screen shot by the way.

---

### Post by falconindy on 2010-01-09
The only reason you might need to upgrade your bootloader would be if you decide to run something exotic like RAID or LVM on your boot partition.

---

### Post by kansasnoob on 2010-01-09
> **mikodo said:**
> I already have an ext3 bootloader booting for Hardy and Karmic. I will be getting rid of the Hardy partition soon to make room for Lucid. I don't use Hardy much anymore. Gparted screenshot below.

Question:

Will it always be OK to boot from an ext3 bootloader in future ext4 FS's or will I eventually have to change it to ext4 also?

Thankyou.

I think you'll be OK if you have grub version (0.97-29ubuntu53) or newer and grub-common version (1.96+20080724-12ubuntu2) or newer.

Otherwise you're liable to have trouble.

---

### Post by AlexandreP on 2010-01-09
I think Mikodo will need to update his bootloader. If I remember correctly, it was Ubuntu 9.04's version of GRUB-Legacy that got patched to be able to boot an OS from an ext4-formatted partition. Versions before would not be able to boot directly an OS from ext4.

But when installing a fresh Lucid Lynx beta version or a final Ubuntu 10.04 release next April, the installer should take care of installing the new GRUB2 bootloader in place of his current GRUB-Legacy (unless he unchecks the option in the advanced installation settings).

---

### Post by mikodo on 2010-01-09
Thanks everyone,

Really good information. I'll reference this as I change things. For now I have newer grub versions, so I'm OK. I'll be sure to watch for the installer to install Grub2 when I install Lucid. As a newbie, I'm sticking to simple partitioning for now, so nothing like raids etc..

Thanks for insight on my screenshot being blurry. I use the screenshot application that is provided by Karmic's Applications > Accessories > Screenshot.  Any suggestions on clearer screenshots? Maybe Shutter??

Mike

---

