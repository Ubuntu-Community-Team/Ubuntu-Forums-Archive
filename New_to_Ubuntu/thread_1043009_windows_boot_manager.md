---
title: "windows boot manager"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by mynameismud on 2009-01-18
okay iv really messed up now i installed ubuntu and grub onto my system but ubuntu woudnt boot it just kept dropping me to a shell (ash) so then i tried to get into xp and it took me a good few times to get into it and only after i went through the live disk. so i manage to get on there and decide ubuntu really isnt going to work as iv been trying to get on for a good 3 days now so foolishly i just delete the partition (it was very late when i did this mind you) so now its the morning and when i try to boot from the hard drive grub just comes up and gives me an error iv only managed to get here because  i had a mandriva live disk lying around. 
so please how do i reinstall the windows boot manager without getting into windows? 

tl:dr how to install windows boot manager without the ability to get into windows .

---

### Post by wizard10000 on 2009-01-18
Start your machine from the Windows install CD, select the recovery console when prompted and run fixboot - that should fix you up.

---

### Post by CLomax on 2009-01-18
Also, if you want to add Ubuntu to the MBR afterwards (assuming you do) use EasyBCD.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by caljohnsmith on 2009-01-18
"fixboot" unfortunately won't fix the problem since that just fixes the Windows partition boot sector. Mynameismud, I think the command you are looking for is "fixmbr" from the Windows Install CD, because that will install a Windows MBR (Master Boot Record) to your HDD so you won't have Grub any more. If you don't have a Windows Install CD, you could instead boot your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And that will also install a Windows MBR. Let us know how it goes.

---

