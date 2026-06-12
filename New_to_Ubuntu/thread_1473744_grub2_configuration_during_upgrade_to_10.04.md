---
title: "grub2 configuration during upgrade to 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Matt26 on 2010-05-05
i'm in the process of upgrading from 9.10 to 10.04 and i've got this window on my screen now for configuring grub2.. it appears to list all of my hard drives or partitions (i can't remember which) with check boxes beside each one in the list.

is this for the selection of which hard drive the OS is installed on or for something else?  i don't want to continue with the installation unless i know exactly what this setup is for, in case i risk choosing the wrong option.

---

### Post by philinux on 2010-05-05
> **Matt26 said:**
> i'm in the process of upgrading from 9.10 to 10.04 and i've got this window on my screen now for configuring grub2.. it appears to list all of my hard drives or partitions (i can't remember which) with check boxes beside each one in the list.

is this for the selection of which hard drive the OS is installed on or for something else?  i don't want to continue with the installation unless i know exactly what this setup is for, in case i risk choosing the wrong option.

Can you post a screenshot?

---

### Post by oldfred on 2010-05-05
Someone posted a screen shot before and this is the problem:

This is what the instructions say (bold by me):
If you're unsure which **drive** is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

It then presents a check box with all **drives and partitions**. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR. Installing to a partition also does not let you boot unless you have another boot loader that lets you chainboot.

If you know which drive your BIOS boots from you should install it there. If you have multiple drives install it to the drive with Ubuntu and in BIOS change to boot from that drive.

---

### Post by Matt26 on 2010-05-05
> **oldfred said:**
> Someone posted a screen shot before and this is the problem:

This is what the instructions say (bold by me):
If you're unsure which **drive** is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

It then presents a check box with all **drives and partitions**. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR. Installing to a partition also does not let you boot unless you have another boot loader that lets you chainboot.

If you know which drive your BIOS boots from you should install it there. If you have multiple drives install it to the drive with Ubuntu and in BIOS change to boot from that drive.

ok, thanks for the details.. so just to make sure i understand this correctly, i should only select the drive- not the partition- where ubuntu is installed?  i do have multiple hard drives but ubuntu is the only OS installed on any of them.

---

### Post by wilee-nilee on 2010-05-05
> **Matt26 said:**
> ok, thanks for the details.. so just to make sure i understand this correctly, i should only select the drive- not the partition- where ubuntu is installed?  i do have multiple hard drives but ubuntu is the only OS installed on any of them.

Yes, but make sure you know which drive it is.

---

