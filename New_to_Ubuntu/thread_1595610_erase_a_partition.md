---
title: "erase a partition"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by kiraku on 2010-10-13
Hi:

The thing is that i have two partititons in my laptop, one with windos xp and the otherone with linux... Now i want to sell it, so i like to erase the linux partition and just let wxp on it...

So how do i do that?...

Do i just erase the partition with gparted form a live cd???... or shoud i do something more???...

Basically, if i erase the partition with gparted, does windows recognize (i don't remember how this word spells) the new space that it has???

i hope you can help me...

cya

---

### Post by AndyM3 on 2010-10-13
No, you should delete the Linux partition and then *resize* the Windows one.

But IMO you should leave Ubuntu as a boot option or install it with Wubi afterwards. Maybe the new user will like it. ;)

---

### Post by Temposs on 2010-10-13
You can use the gparted CD. That will work just fine.

I think what you'll want to do is two operations:
1) Delete the Linux partition
2) Resize the Windows partition so that it takes up the entire drive.

---

### Post by Elfy on 2010-10-13
[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

Reinstall the windows bootloader THEN remove the partition.

---

### Post by kiraku on 2010-10-13
> **Temposs said:**
> You can use the gparted CD. That will work just fine.

I think what you'll want to do is two operations:
1) Delete the Linux partition
2) Resize the Windows partition so that it takes up the entire drive.


yeah, that its!

---

### Post by kiraku on 2010-10-13
> **forestpiskie said:**
> [http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

Reinstall the windows bootloader THEN remove the partition.


thanxz, that really has helpful...

---

### Post by kiraku on 2010-10-13
> **forestpiskie said:**
> [http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

Reinstall the windows bootloader THEN remove the partition.


hi... after installing the bootloader, do i erase de partition from windows or linux??

---

