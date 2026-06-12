---
title: "How do i untstall Ubuntu from dual boot  on XP"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by rubytru on 2010-08-14
I love Ubuntu, but, after having rushed in to install it as a dual boot on my sisters PC, I can't get into either ...

Ubuntu doesn't let me log in and XP won't boot.  

So now my sister is freaking out.  I've given it my best shot for now but must learn more before venturing to do this again on any PC but my own.

Thank you for all the support you give.

---

### Post by rubytru on 2010-08-14
I love Ubuntu, but, after having rushed in to install it as a dual boot on my sisters PC, I can't get into either ...

Ubuntu doesn't let me log in and XP won't boot.  

So now my sister is freaking out.  I've given it my best shot for now but must learn more before venturing to do this again on any PC but my own.

Thank you for all the support you give.

---

### Post by cariboo on 2010-08-14
Boot from your XP install CD and once at the install screen select R for the repair console. On you are at the repair console prompt, type:

```
fixboot c:
```

The above command should remove grub from the mbr and replace it with with Windows boot sector.

I would suggest you backup all your sisters important data using the Live CD, before trying to fix the mbr, as you may end up with a corrupted partition table. Once you are back in Windows you can use the disk management tools to remove the Ubuntu partition. Next you can use gparted on the Live CD to resize the Windows partition.

---

### Post by rubytru on 2010-08-14
Thankyou cariboo907  ...

---

### Post by cariboo on 2010-08-14
I merged your two threads.

---

