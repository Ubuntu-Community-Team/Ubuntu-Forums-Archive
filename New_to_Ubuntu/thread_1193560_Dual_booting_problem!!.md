---
title: "Dual booting problem!!"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by cusinmex on 2009-06-21
it seems that i have 3 ubuntu partitions on my HD :S
when i get to black screen at start up there are
2 ubuntus and then theres win xp. when i select win xp
it goes to another black screen to choose either xp or ubuntu :/

and then the OS loads..
but **how do i make it so that i only have one Ubuntu option and the XP?**

BTW...i had previously uninstalled ubuntu
and even after i uninstalled it.. i shut down the pc
and it would ubuntu would still run even though i uninstalled

thx

---

### Post by raymondh on 2009-06-21
> **cusinmex said:**
> it seems that i have 3 ubuntu partitions on my HD :S
when i get to black screen at start up there are
2 ubuntus and then theres win xp. when i select win xp
it goes to another black screen to choose either xp or ubuntu :/

and then the OS loads..
but **how do i make it so that i only have one Ubuntu option and the XP?**

BTW...i had previously uninstalled ubuntu
and even after i uninstalled it.. i shut down the pc
and it would ubuntu would still run even though i uninstalled

thx


Hola Cusinmex,

Kindly post

```
sudo fdisk -l
```
```
cat /boot/grub/menu.lst
```

(small L not number 1).

Did you have a WUBI installation as well?  Just getting as much info from you as possible.

---

### Post by presence1960 on 2009-06-21
> **raymondhenson said:**
> Hola Cusinmex,

Kindly post

```
sudo fdisk -l
```
```
cat /boot/grub/menu.lst
```

(small L not number 1).

Did you have a WUBI installation as well?  Just getting as much info from you as possible.

Sounds like he does have a wubi installation -> > when i select win xp
it goes to another black screen to choose either xp or ubuntu :/

But to be sure of exactly what he has he should download the Boot Info Script to his desktop from here : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Once downloaded to your desktop open a terminal by going Applications > Accessories > Terminal. When terminal opens run this command > sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file on your desktop. This file has all the info about your setup and boot info. Open the file and paste the contents back here. Once pasted on here highlight all text and click # on the toolbar to place code tags around the text. Then we will see exactly what you have on your rig.

> BTW...i had previously uninstalled ubuntu
and even after i uninstalled it.. i shut down the pc
and it would ubuntu would still run even though i uninstalled
Did you remove Ubuntu by deleting or formatting it's partition? If so you still have GRUB on your MBR that is why GRUB is displaying when you boot! That is no problem!

---

### Post by raymondh on 2009-06-21
hello Presence1960 

... ah yes, the bootinfoscript.  That's a GOOD tool.

... good catch on the 'GRUB in MBR' thought.

Happy father's day.

---

### Post by presence1960 on 2009-06-21
Happy Fathers Day to you also Raymond. And all the other Dads on here!!

---

### Post by gwyndyn on 2009-06-21
Are you sure they are separate partitions, or are they just old versions of the kernel?  Look at the version number for each one when you boot up. If they are just old versions of the kernel, there's a way to remove those options from grub, but I don't know how to do it. I'm sure someone here can help you with it. :)

---

