---
title: "making logical partition as active to load grub!!!"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-08-29
I have installed ubuntu on one logical partition under extended partition as shown in picture. But due to some reason it got inactive now what i have to give command after ```
sudo grub
```
that will make the logical partition to load on startup.

---

### Post by loomsen on 2009-08-29
o.O

Where did you install the bootloader to? And what does it show?

You don't have any partition marked as bootable, plus booting from a logical partition requires additional modules in your initrd.img to be able to boot from. 

But this doesn't look good to be honest.

Each and every Documentation tells you you should _not_ try and boot from an ext4 partition.

Thats another reason why, however, it's not lost, but you'll probably save yourself some time if you read a introduction and then reinstall (chosing a different layout)

Make at least a separate /boot partition, ext3, 300MB should be sufficient.

---

### Post by eshant_engineer on 2009-08-29
/boot is in the same partition i.e 'ext4' partition. It is the root '/' for ubuntu.

---

### Post by loomsen on 2009-08-29
Mexico is the same as Hawaii, it's in Canada?

You won't be able to boot from a logical volume without a bootloader initializing a proper initrd, which includes the proper modules.

---

### Post by louieb on 2009-08-29
Not a problem. Linux does not care  primary or logical  partition, boot flag set or not it just does not matter.

Anyway After you enter **sudo grub**  at the **grub> **prompt 
1st check for main grub program

```
find /boot/grub/stage2
```should in your case return **(hd0,8)** if it does not then there is a problem and you need to stop right there. 

If it does return (hd0,8) then
```
root (hd0,8)
setup (hd0)
quit
```and you should be all set

---

