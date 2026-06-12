---
title: "How to increase ubuntu partition?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by karmi on 2009-12-20
Hello, I want to increase my ubuntu partition by 2 GB, and I'm planning to take those 2 GB from another partition . so is there a software tool that can perform this for ubuntu?

Note: I use Ubuntu 9.10 (Karmic Koala) 64 bit

---

### Post by Nick11202 on 2009-12-20
apt-get install gparted

---

### Post by zeroseven0183 on 2009-12-20
Use the command above to install Gparted. Then follow the instructions in [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

Be sure to make backups before you do anything else. Hope that helps!

---

### Post by Yvan300 on 2009-12-20
You would have to boot from the live cd because you cannot change the partitions when they are in use ie when you are using ubuntu. The live cd has gparted on it. Go to system > administrator >gparted

---

### Post by EnGorDiaz on 2009-12-20
> **Yvan300 said:**
> You would have to boot from the live cd because you cannot change the partitions when they are in use ie when you are using ubuntu. The live cd has gparted on it. Go to system > administrator >gparted

its because the partitions are system and mounted at the same time

---

