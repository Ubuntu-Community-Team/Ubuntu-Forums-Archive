---
title: "Remove Mint."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Kapser on 2010-04-30
Well, i've searched the forums and googled the topic but i couldn't find anything i could understand.
Basically i dual boot Mint 8 and Ubuntu 10.04 (just upgraded from 9.10 yesterday) and i want to remove Mint 8 and make ubuntu 10.04 the only OS on my computer.So how do i do it ? 
cheers

---

### Post by swoll1980 on 2010-04-30
> **Kapser said:**
> Well, i've searched the forums and googled the topic but i couldn't find anything i could understand.
Basically i dual boot Mint 8 and Ubuntu 10.04 (just upgraded from 9.10 yesterday) and i want to remove Mint 8 and make ubuntu 10.04 the only OS on my computer.So how do i do it ? 
cheers

Use Gparted, and delete the partition that contains mint. Then expand your Ubuntu partition.  Depending on where grub is you may have to fix it, so grab a grub disk just in case.

---

### Post by Kapser on 2010-04-30
Thanks, but from where do i get a grub disk ?

---

### Post by swoll1980 on 2010-04-30
> **Kapser said:**
> Hmm...... How ? What do u suggest i should use ?

Gparted. While logged into Ubuntu
```
sudo apt-get install gparted
```

---

### Post by swoll1980 on 2010-04-30
> **Kapser said:**
> Thanks, but from where do i get a grub disk ?

[Grub2]("ftp://alpha.gnu.org/gnu/grub/") 

If you installed Ubuntu after mint you shouldn't have to mess with grub. But if you're going to play with Linux you need to always have a grub disk handy. You can google for gparted, and grub instructions.

---

