---
title: "Problem resolving dependencies during packet installation"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by s.v.z on 2010-05-04
Hi. I need to install jre and jdk. **Unfortunately I can`t install them from the repositories**, but I have all the files on my HDD. There are 3 .deb packets. The problem is that when I try to install **sun-java6-jre_6.20dlj-0ubuntu1.9.10_all.deb**, the packet manager says it requires **sun-java6-bin_6.20dlj-0ubuntu1.9.10_i386.deb** and vice versa =). How can I solve that?

---

### Post by xumuk37 on 2010-05-04
why don't you just do ```
sudo apt-get update
sudo apt-get install sun-java6-sdk sum-java6-*
```

---

### Post by s.v.z on 2010-05-04
As I wrote in my first post, I`m having a pretty shitty mobile internet connection right away, so I can`t install from the reps.

---

### Post by xumuk37 on 2010-05-04
ouch... sorry, I have not seen it...

---

### Post by tristan.cole on 2010-05-04
try first copying those 2 files to the folder: /var/chache/apt/archives/ - as a sudo user, then try to install through terminal it should pick those 2 files up and install them

---

