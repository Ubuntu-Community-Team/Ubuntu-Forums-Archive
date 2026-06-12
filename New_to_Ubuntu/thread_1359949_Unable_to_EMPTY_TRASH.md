---
title: "Unable to EMPTY TRASH???"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by kapmsd on 2009-12-20
Hi guys!!!I use Ubuntu 8.04(gnome).
I am not able to empty the trash due to some reasons.
Currently trash has 5 to 6 folders  which i deleted from my desktop.
When i do EMPTY TRASH option,it looks like it works but it is not emptying the trash contents.
Even when i try to delete each folder individually,it doesn't work stating that i don't have the permission to do it.
Pls provide ur valuable inputs guys!!!!!

---

### Post by Troll_the_Great on 2009-12-20
> **kapmsd said:**
> Hi guys!!!I use Ubuntu 8.04(gnome).
I am not able to empty the trash due to some reasons.
Currently trash has 5 to 6 folders  which i deleted from my desktop.
When i do EMPTY TRASH option,it looks like it works but it is not emptying the trash contents.
Even when i try to delete each folder individually,it doesn't work stating that i don't have the permission to do it.
Pls provide ur valuable inputs guys!!!!!

Try with this command:
```
sudo rm -fr  ~/.local/share/Trash/files/*
```
Cheers!

---

### Post by gs777 on 2009-12-20
$ sudo nautilus
then goto trash and try to delete

---

