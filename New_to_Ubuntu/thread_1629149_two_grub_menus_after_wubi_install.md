---
title: "two grub menus after wubi install"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by mikhaell on 2010-11-23
hello,

i recently installed ubuntu 10.10 through WUBI, and kept windows XP. everything works fine, but when i startup my computer, i get asked weather i want to startup ubuntu or windowsxp- after selecting ubuntu, i get to another menu (headlined Grub menu this time) asking the same question again (this time giving me the recovery mode option for ubuntu as well). Is there any way to delete one of these menus?

---

### Post by drs305 on 2010-11-23
> **mikhaell said:**
> hello,

i recently installed ubuntu 10.10 through WUBI, and kept windows XP. everything works fine, but when i startup my computer, i get asked weather i want to startup ubuntu or windowsxp- after selecting ubuntu, i get to another menu (headlined Grub menu this time) asking the same question again (this time giving me the recovery mode option for ubuntu as well). Is there any way to delete one of these menus?

You installed within Windows, so the first menu you see is the Windows-created menu (the contents are in the boot.ini file). Once you select Ubuntu from the Windows menu you are transferred to the Ubuntu/grub menu. 

Since your Ubuntu install is actually a file within Windows, you go through the Windows menu to get to it.

---

### Post by mikhaell on 2010-11-23
thanks! and if I am happy with the ubuntu install, can i make it its own partition or do i need to re-install everything?

or erase windows completely?

---

### Post by drs305 on 2010-11-23
If you haven't made a lot of customizations, the easiest thing to do would be to create a new partition and just do a fresh (normal) install. If you create the partition first, you would select manual partitioning during the install. Otherwise Ubuntu will offer to install it by sharing the disk space with Windows. You have more control over where and how large you want the Ubuntu installation by making the partition first.

I wouldn't remove Windows if you can afford the space. It's not bad to have it to fall back on if and when you need it. Personally, I don't have Windows on my main machine but wouldn't remove it if it were already installed.

---

