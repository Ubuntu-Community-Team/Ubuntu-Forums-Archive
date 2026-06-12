---
title: "Triple boot : GRUB not showing all 3"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by darkstarbenji on 2009-09-08
I had windows and Ubuntu duel booting and decided to try out Debian. I thought (stupid me) that the grub would show both ubuntu and debian. Now i only see debian and windows. any way to get all 3 on the menu?? thanks in advance

---

### Post by jonathanysp on 2009-09-08
you can simply edit the /boot/grub/menu.lst file. this file basically tells grup what options there are in the boot menu. Im not exactly sure what to add, maybe you can search around, but you only need to add an entry for ubuntu and tell grub where ubuntu is on your hdd.

---

### Post by rajeev1204 on 2009-09-08
> **darkstarbenji said:**
> I had windows and Ubuntu duel booting and decided to try out Debian. I thought (stupid me) that the grub would show both ubuntu and debian. Now i only see debian and windows. any way to get all 3 on the menu?? thanks in advance

From a terminal do this.

```
sudo gedit /boot/grub/menu.lst
```

Then read this file and there are some sample entries on how the entry should be for various operating systems.

Scroll down to the near end of the file and add the corresponding entry for your ubuntu.

You will need to find the partition where ubuntu is installed which will be displayed like so

```
sudo fdisk -l
```



regards

rajeev

---

### Post by darkstarbenji on 2009-09-08
> **rajeev1204 said:**
> From a terminal do this.

```
sudo gedit /boot/grub/menu.lst
```

Then read this file and there are some sample entries on how the entry should be for various operating systems.

Scroll down to the near end of the file and add the corresponding entry for your ubuntu.

You will need to find the partition where ubuntu is installed which will be displayed like so

```
sudo fdisk -l
```



regards

rajeev



Thank you both for your responses but when i type sudo fdisk -l it says command not found. might it be another command for debian thats different from ubuntu?

---

### Post by darkstarbenji on 2009-09-08
i should also probably mention that windows/debian is on one hard drive and ubuntu is on seperate one.

---

### Post by LewRockwell on 2009-09-08
> **darkstarbenji said:**
> Thank you both for your responses but when i type sudo fdisk -l it says command not found. might it be another command for debian thats different from ubuntu?

it's a dash little "L"...not a one...

.

---

### Post by LewRockwell on 2009-09-08
> **darkstarbenji said:**
> i should also probably mention that windows/debian is on one hard drive and ubuntu is on seperate one.

so Debian installed it's grub which has Debian and Windows listed, but not Ubuntu(which is on another hard drive)

the easiest thing to do is use a LiveCD of some *nix distro(we use Puppy Linux) to open the /boot/grub/menu.lst in the Debian partition(which is the grub menu.lst file that the part of grub in your Master Boot Record is pointing to)

and to also open the /boot/grub/menu.lst in the Ubuntu partition

then you can just copy, paste, and edit(if necessary) the relevant entries from the ubuntu menu.lst to the debian menu.lst

this is actually easier and immensely more fun that it sounds at first

before you start messing with either file you might want to make a backup copy

usually that's done something like this:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```remember to do it for both the debian one and the ubuntu one

.

---

### Post by darkstarbenji on 2009-09-08
Worked like a charm! Thank you everyone!:guitar:

---

### Post by raymondh on 2009-09-08
EDIT :  congratulations.

---

