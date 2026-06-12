---
title: "Need help with GRUB and Chainloading TrueCrypts MBR"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-03-30
I am in desperate need of some help. I have a dual boot system, with Ubuntu and Vista. I had everything working, until a couple days ago I kind of erased my boot partition. I have Vista encrypted with TrueCrypt and saved a copy of the MBR that TrueCrypt installed. But I used to follow the guide [here]("http://ph.ubuntuforums.com/showpost.php?p=4786419&postcount=10"), but it no longer is working. Can someone please help me? 

I have the TrueCrypt.mbr and TrueCrypt.backup copied to the /boot partition, that is where they were before. But now I need to setup GRUB.

My partition scheme is also,
```
sda1 -> Vista
sda2 -> Boot
sda3 -> SWAP
sda4 -> /
```

---

### Post by slughappy1 on 2009-03-30
Turns out I needed to add this at the bottom

title Windows Vista/Longhorn
rootnoverify (hd0,0)
makeactive
chainloader (hd0,1)/truecrypt.mbr
boot

---

