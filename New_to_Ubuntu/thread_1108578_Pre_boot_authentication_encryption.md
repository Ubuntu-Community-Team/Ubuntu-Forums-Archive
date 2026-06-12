---
title: "Pre boot authentication encryption"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by alanfang on 2009-03-27
Is there a way to have an encrypted system and pre boot authentication on ubuntu? Truecrypt offers this for windows only but I was wondering if there was an alternative for linux. Thanks.

---

### Post by mrsteveman1 on 2009-03-27
Gotta download the [alternate install cd]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate"), there is an option for encryption during installation :)

---

### Post by alanfang on 2009-03-27
So I would have to reinstall the whole OS? If possible I would rather not, it took me 3 days to get it to work the first time around.

---

### Post by mrsteveman1 on 2009-03-28
Well, there are ways to encrypt the system in place but it is very complicated.

---

### Post by hyper_ch on 2009-03-28
there is no real pre-boot authentication on linux. You'll have (this far) an unencrypted initrd in your /boot partition.

It is however possible to encrypt the rest of the system. Even after installation but I wouldn't recommended it to try as you'll have to mess with your partitions and you can easily screw up there (well, it shouldn't matter as you should have backups anyway).

---

