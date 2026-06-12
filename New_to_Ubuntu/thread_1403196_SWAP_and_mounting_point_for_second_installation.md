---
title: "SWAP and mounting point for second installation"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-10
My computer has several hard disks. On the first one I have 9.10 installed and it has its own SWAP space. Now I want to install another Ubuntu on the second hard disk, do I need to reserve space for SWAP another time or will it be able to use the SWAP on the first hard disk?? 
Secondly, regarding the mount point for the second installation. Should it also be set to '/' like I normally did on the first one or just leave it empty?
Thanx in advance.

---

### Post by HappyFeet on 2010-02-10
> **SteelCore said:**
> My computer has several hard disks. On the first one I have 9.10 installed and it has its own SWAP space. Now I want to install another Ubuntu on the second hard disk, do I need to reserve space for SWAP another time or will it be able to use the SWAP on the first hard disk?? 
Secondly, regarding the mount point for the second installation. Should it also be set to '/' like I normally did on the first one or just leave it empty?
Thanx in advance.

Yes, "/" will do, since you need a mount point to install. Secondly, unless you are in dire need of space, why not just let ubuntu make a new swap space? (or make swap of the size you choose) Keep it simple.

---

### Post by coffeeaddict22 on 2010-02-10
Hi,
You get asked during install - the manual partition phase-  where you want the swap, and Linux distributions will generally share a swap file between them.

---

