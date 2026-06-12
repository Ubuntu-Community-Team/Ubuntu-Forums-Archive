---
title: "boot loader"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mojolobo on 2009-05-17
I have two hdd , ive installed my xp first on the first then ubuntu 9.04 on the other . 
My question is 
Where is the boot loader located .

If i removed either hdd , will i be able to boot into my either os.

thanks

---

### Post by nhasian on 2009-05-17
by default the boot loader is on your primary boot disk which is probably your windows computer.  if you remove your windows hard disk, neither OS will boot.

---

### Post by sideffects on 2009-05-17
Nevermind.

---

### Post by mojolobo on 2009-05-17
How do i get them to boot independently. ?

---

### Post by logos34 on 2009-05-17
like nhasian says, grub is on the windows disk...Reinstall grub to the ubuntu disk and then you can remove windows disk and still boot:

so if ubuntu is sdb:
> 
sudo grub-install /dev/sdb (--> writes grub IPL/stage1 to MBR of that disk)

---

### Post by mojolobo on 2009-05-17
thanks for all the imput guys . Really appreciate it

---

### Post by -kg- on 2009-05-17
An alternative is to install the bootloader for each OS to the MBR of the hard drive it is located on.  Then, in order to boot to one or the other, all you have to do is go into BIOS and change the boot order of the hard drives.

---

