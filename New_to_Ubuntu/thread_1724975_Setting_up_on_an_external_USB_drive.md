---
title: "Setting up on an external USB drive"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by loseby on 2011-04-09
I intend getting an USB3 hard drive ( mobo has USB3 ) and want to install Ubuntu on that. The idea is when I need to use linux I will trun the USB hard drive on and boot from it.


I have Ubuntu on another PC dual boot but have had problems after problems. 

Any problems with doing what I want or any hints ?

---

### Post by C.S.Cameron on 2011-04-09
> **losbey said:**
> I intend getting an USB3 hard drive ( mobo has USB3 ) and want to install Ubuntu on that. The idea is when I need to use linux I will trun the USB hard drive on and boot from it.


I have Ubuntu on another PC dual boot but have had problems after problems. 

Any problems with doing what I want or any hints ?

I have heard that Ubuntu does not boot from USB3 but can't confirm.
Otherwise I would suggest disabling the internal drive first to prevent grub problems.
Then plug in the external and install as usual.
You may want to make the first partition NTFS so you can swap data with Windows machines.
I would not see any problem booting if the boot manager is on another drive, perhaps mentioned in the internal drives grub2.

---

### Post by loseby on 2011-04-09
> **C.S.Cameron said:**
> I have heard that Ubuntu does not boot from USB3 but can't confirm.

well thats what I need to find out

> **C.S.Cameron said:**
> 
I would not see any problem booting if the boot manager is on another drive, perhaps mentioned in the internal drives grub2.
Otherwise I would suggest disabling the internal drive first to prevent grub problems.

Definitely want GRUB on the USB drive......dont want GRUB near my Windows drives....will make the USB the first boot device

---

