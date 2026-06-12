---
title: "GRUB editing"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by spacemonkeyxxx on 2009-12-30
I succesfully installed UBUNTU 9.10 yesterday and now that works fine, however Vista has died.
 
When I try to boot a program called GRUB starts and offers me a bunch of booting options. The only option for vista is sda1, which is the system recovery partition, and thus it asks for my recovery disks which I don't have with me. I think I should be booting Vista from sda2. Is there any way of telling GRUB to boot from sda2 instead of sda1? It gives me an option to enter a command line, but I have no idea what the command would be.

---

### Post by lindsay7 on 2009-12-30
Try this first. Type in the terminal 

 "sudo update-grub"  without the quotation marks

---

### Post by bumanie on 2009-12-30
Hope you haven't accidentally removed vista - post the output of > sudo fdisk -lThis will list all the partitions on the computer.

---

### Post by spacemonkeyxxx on 2009-12-30
Nice one, worked first time.

---

