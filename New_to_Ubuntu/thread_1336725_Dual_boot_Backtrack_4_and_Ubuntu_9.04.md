---
title: "Dual boot Backtrack 4 and Ubuntu 9.04"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by k33bz on 2009-11-24
Ok, so far everytime I google on how to do this it is either dual boot with XP or it refers back to backtrack (the first one). I want to know what steps I do to dual boot both backtrack 4 with ubuntu 9.04. I already have Ubuntu 9.04 on my laptop.

Only thing I know for sure I have to do is use gpart so I can shrink my Ubuntu partition. Not sure what I will have to do after that. All help is welcomed. 

Thanks

---

### Post by cherva on 2009-11-24
1) Shrink your partition so you can install Backtrack on the new partition
2) Boot from the Backtrack CD and install as normal just be sure to select the right partition and don't make another swap partition because you can use your current one.
3) If by some chance after the reboot you end up in booting only the backtrack without GRUB asking you what do you want to boot you can do a little googling about how to add your ubuntu install into the boot options of GRUB

---

### Post by k33bz on 2009-11-24
> **cherva said:**
> 1) Shrink your partition so you can install Backtrack on the new partition
2) Boot from the Backtrack CD and install as normal just be sure to select the right partition and don't make another swap partition because you can use your current one.
3) If by some chance after the reboot you end up in booting only the backtrack without GRUB asking you what do you want to boot you can do a little googling about how to add your ubuntu install into the boot options of GRUB

As far as I know backtrack 4 does not have an installer.

---

### Post by nc6j on 2009-11-24
> **k33bz said:**
> As far as I know backtrack 4 does not have an installer.

root@bt:~# ubiquity

---

### Post by cherva on 2009-11-27
It's nice to mark your thread as SOLVED if you got it working ...

---

### Post by k33bz on 2009-11-27
> **cherva said:**
> It's nice to mark your thread as SOLVED if you got it working ...
Sorry I usually do do that, just been busy trying to configure BT4 since I installed it.

---

