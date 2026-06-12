---
title: "cant copy files"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by amiacamal on 2011-08-03
Im booted from a live cd (broke my install, trying to get my files back before ire install) trying to copy from the hdd to an external harddrive. it says i dont have permission, so how do i get it? I need to get permissions for basically everything in the home folder...

---

### Post by TeoBigusGeekus on 2011-08-03
Try opening nautilus from a terminal with
```
gksu nautilus
```

---

### Post by amiacamal on 2011-08-03
no luck :/ says i dont have read permissions. im copying FROM the hdd of the laptop TO an external HDD, through a live cd..

---

### Post by Jouke S on 2011-08-03
try sudo mv /media/further/path/ /media/further/path/
the first path is where the files are located, second where you would like them moved.

---

### Post by haqking on 2011-08-03
> **amiacamal said:**
> no luck :/ says i dont have read permissions. im copying FROM the hdd of the laptop TO an external HDD, through a live cd..

i take it you are the owner ? and supplying correct sudo credentials ?

---

### Post by amiacamal on 2011-08-03
Its my laptop, but im not sure it knows that :/ how can it from the live CD? what exactly counts as the correct sudo credentials? The live cd doesnt ask for a password!

---

### Post by Jouke S on 2011-08-03
If a sudo command doesn't ask for a password, it means you already have elevated rights. 
When your command returns nothing (blank) it's likely to have been successful.

---

### Post by amiacamal on 2011-08-03
sudo chmod +rw home

Job done :) i think

---

