---
title: "i lost my dual boot after i install a fresh vista"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by msayerh on 2009-08-04
i use to dual boot between vista and ubuntu 
now that i uninstall vista and install a fresh one, i lost the menu of dual boot 
when i turn my pc pn or restart it goes automaticly to vista 
vista on C and ubuntu on E 
how can i get it to work again like before ?
HELP PLZ

---

### Post by Clorow on 2009-08-04
Ubuntu is still there. I know there's a guide for this, but I don't remember where. Someone will probably post it, hopefully.

---

### Post by lisati on 2009-08-04
Have a look here in the section "recovering Grub after installing Windows": [https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

---

### Post by bumanie on 2009-08-04
As long as you have installed vista to the same partition as before, follow [this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by prshah on 2009-08-04
> **msayerh said:**
> vista on C and ubuntu on E 

> **lisati said:**
> Have a look here in the section "recovering Grub after installing Windows": [https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

You can use the above option if you have installed Ubuntu in it's own partition and are using GRUB as your bootloader. 

However, if you have installed using Wubi ("within windows" installation) then you need to follow the instructions at [this link]("http://ubuntuforums.org/showpost.php?p=7563772&postcount=3")

Post back if you are not sure which type on installation you have performed, or if you have any problems.

---

### Post by lisati on 2009-08-04
> **lisati said:**
> Have a look here in the section "recovering Grub after installing Windows": [https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

Just a thought: the above link will be of most value if (a) Ubuntu was installed in its own partition, **and** (b) the fresh install of Windows did not overwrite Ubuntu's partition.

---

### Post by msayerh on 2009-08-04
> **lisati said:**
> Have a look here in the section "recovering Grub after installing Windows": [https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)



now when i do sudo grub 
grub > root (hd0,2)    i have one hard drive and ubuntu on the E drive 
it goes fine but when  i type setup (hd0) it give me this error 
Error 17: Cannot mount selected partition
and i have no idea why 
any help will be gr8

---

