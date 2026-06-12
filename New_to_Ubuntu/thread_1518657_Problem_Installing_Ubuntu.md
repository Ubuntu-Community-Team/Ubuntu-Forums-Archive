---
title: "Problem Installing Ubuntu"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by MarvinVzla on 2010-06-26
Hello, please sorry my bad English, I had a big problem I had been using Ubuntu for 1 year and I just buy a new laptop a HP Pavilion dm3 with intel core duo 2, I had tried to install ubuntu like I had in my old laptop but I can not go pass the partition because I had a HD 500gb and this laptop had 3 partition all ready, 1 for recovery, another for Microsoft and the last one is the smallest i do not know what it does, so I took the biggest parts that is the one for windows so i just leave it 100gb for it and the rest 350gb free for ubuntu, so when i want to install the install system tells me that this 350gb are useless, and when i go back to windows (i leaved because i used at my office) in only appear the 100gb, what can i do to use this 350gb for ubuntu?
Thank you so much for all the help that you can gave me

---

### Post by lukeiamyourfather on 2010-06-26
What label and format is on the 350GB in the partition section of the installer? Does it say its free or does it show it as NTFS or some other format?

---

### Post by -humanaut- on 2010-06-26
From the Ubuntu live cd open a terminal and type

cat /etc/fstab

post back the output.

---

### Post by lukeiamyourfather on 2010-06-27
> **-humanaut- said:**
> From the Ubuntu live cd open a terminal and type

cat /etc/fstab

post back the output.

I think you mean this.

```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2010-06-28
Better yet is "sudo fdisk -lu"  That's a lowercase L, not a one.

---

