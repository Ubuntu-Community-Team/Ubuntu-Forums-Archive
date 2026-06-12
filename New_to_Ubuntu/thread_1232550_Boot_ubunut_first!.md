---
title: "Boot ubunut first!"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-05
Hello.

When i boot up my PC and the dual boot screen apears it automatically boots windows first (if i don't choose ubuntu) is there a way i can change it and make it boot ubuntu before windows.
Thanks.

---

### Post by blur xc on 2009-08-05
I don't remember the exact path but you need to edit your menu.lst (/boot/grub/menu.lst??)  I just did it a couple of days ago.

Just copy the section for widows and paste it under the ubuntu section and it will reorder in the boot menu.

BM

---

### Post by jacklinux on 2009-08-05
How do i get to these grub lists? inside ubnutu or windows

---

### Post by terry_gardener on 2009-08-05
easier gui way to do this. 
install startupmanager package and there is an option within there for default os select the one that you want. 

thats it.

---

### Post by django0909 on 2009-08-05
Get yourself into Ubuntu, and open a terminal.

Type this:

```
sudo gedit /boot/grub/menu.lst
```

Provide your password when asked, and in the file that opens, add the following to the bottom.

```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```

Reboot the machine

This *should* sort you out, provided Windows and Ubuntu are on the same drive. It will add 'Windows XP' to your boot list.

If it doesn't work, change hd0,0 to hd0,1



If I've got that wrong, someone please let me know!

-django

---

### Post by candtalan on 2009-08-05
> **jacklinux said:**
> Hello.
When i boot up my PC and the dual boot screen apears it automatically boots windows first (if i don't choose ubuntu) is there a way i can change it and make it boot ubuntu before windows.
Thanks.

Be aware - that if you installed via WUBI, into Windows, then you will get what you describe, and also you will be using the Windows boot loader, not grub in the 'normal' way I think.

Did you install *into* Windows?

---

### Post by philinux on 2009-08-05
Dont do anything till you respond to this post ^^^

---

### Post by LewRockwell on 2009-08-05
> **django0909 said:**
> Get yourself into Ubuntu, and open a terminal.

Type this:

```
sudo gedit /boot/grub/menu.lst
```If I've got that wrong, someone please let me know!

-django

should be:```
**gksudo gedit /boot/grub/menu.lst
```**use "sudo" when initiating "things that run, start to finish, in the terminal(command line interface)"

use "gksudo" when initiating "things that run in a window(graphical user interface)"

.

---

### Post by LewRockwell on 2009-08-05
also you might want to make a back-up copy of your menu.lst **BEFORE** you start changing things...```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

.

---

