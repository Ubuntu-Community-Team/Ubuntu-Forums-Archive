---
title: "grub error22 no dual boot"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by muted1987 on 2009-04-05
Most error 22's from the grub that i have seen are due to dualbooting but i am not so i thought id ask anyway.

Right so i woke up this morning to find that my grub has an error. error22 to be precise.

The only thing i changed was that i added a new slave and added the /etc/fstab line to auto mount the drive but surely that can be the cause.

Anyone know how to fix this?

ok so i found that gparted cant find the /dev/sda cant be found via live cd

---

### Post by lswest on 2009-04-05
Can you boot to a liveCD and post the contents of /boot/grub/menu.lst (from your hard drive, so mount it first) and ```
sudo fdisk -l
sudo blkid
``` from the terminal?

---

### Post by muted1987 on 2009-04-05
thanks for the idea lswest but i made a silly schoolboy error and dindt check to make sure the cables were in properly, and itlooks like one came loose.

seems to boot up fine thanks again

---

### Post by lswest on 2009-04-05
> **muted1987 said:**
> thanks for the idea lswest but i made a silly schoolboy error and dindt check to make sure the cables were in properly, and itlooks like one came loose.

seems to boot up fine thanks again

No problem, it's always nice when problems turn out to be something easy :P

---

