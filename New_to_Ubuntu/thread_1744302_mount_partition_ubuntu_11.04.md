---
title: "mount partition ubuntu 11.04"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by anhito on 2011-04-30
my hardisk have 3 partition and 1 swap (sda5), sda1 for ubuntu, sda6 for data (ext4), sda7 for data(fat32)
I just upgrade ubuntu from 10.10 to 11.04, but not success.
now, i use live - usb ubuntu 11.04, and i can't open partition sda6  and display "**The folder contents could not be displayed.** You do not have the permissions necessary to view the contents of "Data"."
So help, how to open this partition in live usb ubuntu 11.04.
thanq

---

### Post by kidwai on 2011-04-30
try installing mountmanager or gparted through the software centre using livecd .. use that to mount the partition .

i dont know the terminal commnads to do so :(

---

### Post by anhito on 2011-05-01
thanq, i solved this problem, when i repaired grub, and i can open all partition.

---

