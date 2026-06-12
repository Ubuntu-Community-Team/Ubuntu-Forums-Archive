---
title: "Partition doesn't show in the Storage Device Manager..?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-12
Hello,

I want to automatically mount hard drive sda4 which is labeled as "Opslag". I installed the Storage Device Manager (as described [here]("http://ubuntuforums.org/showthread.php?t=872197")) and opened it. 

The problem is however, that I don't see sda4. I see sda1 and sda2, but not sda4 (sda3 is swap, but I don't see that one either). Does it have anything to do with the label? Or is there any other reason why it is not showing up?

---

### Post by Dynaflow on 2009-05-12
What's the output of ```
sudo fdisk -l
```

---

