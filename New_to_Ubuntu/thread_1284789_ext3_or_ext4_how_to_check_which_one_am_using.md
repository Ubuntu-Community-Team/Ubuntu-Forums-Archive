---
title: "ext3 or ext4 how to check which one am using?"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2009-10-07
Sorry for the daft question but I installed Ubuntu 9.04 some moons back and I forgot which file-system I chose during installation. 

Is there a command I can type which would tell me?

Cheers

---

### Post by Paqman on 2009-10-07
> **terrykiwi83 said:**
> 
Is there a command I can type which would tell me?


Probably, but i'd just open up Gparted and have a look.

---

### Post by akudewan on 2009-10-07
```
mount
```

It will show you a list of all mounted partitions along with the type.

---

### Post by Cheezespread on 2009-10-07
```
df -T
```

or ```
mount 
```

---

### Post by dwasifar on 2009-10-07
If you didn't partition manually, you have ext3.  

To get ext4 in Jaunty you have to bypass the guided partitioning and set up each partition manually, which you'd probably remember doing.  :)

---

### Post by terrykiwi83 on 2009-10-07
Thanks for the quick replies. Turns out I have ext4. :)

---

### Post by nhasian on 2009-10-07
> **terrykiwi83 said:**
> Thanks for the quick replies. Turns out I have ext4. :)

wow good job.  now your ready for Karmic Koala :)

---

