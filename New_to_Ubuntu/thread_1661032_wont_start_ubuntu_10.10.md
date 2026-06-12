---
title: "wont start ubuntu 10.10"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by bayon on 2011-01-06
i turned off my ubuntu, but dint wait till it completely turns off and switched off electricity, and now i cant start it.

this is what it shows and the same shows in recovery mode
[IMG]http://img140.imageshack.us/img140/6749/06012011204.jpg[/IMG]

---

### Post by XeonBloomfield on 2011-01-06
It's looking like partitions are destroyed.

Probably allocation table is damaged.

---

### Post by bayon on 2011-01-06
> **XeonBloomfield said:**
> It's looking like partitions are destroyed.

Probably allocation table is damaged.

so, what i can do? atleast, to get my files?

---

### Post by XeonBloomfield on 2011-01-06
I think that another partitions are accessible.

Run LiveCD and mount available partitions.

---

### Post by Rubi1200 on 2011-01-06
Hi and welcome to the forums :-)

Use a LiveCD to boot the computer and save your files by running Nautilus as root (gives you access without permissions problems).
```
gksu nautilus
``` in the terminal (Applications > Accessories > Terminal).

At the same time, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we can take a look.

---

### Post by bayon on 2011-01-06
boot info script in terminal shows:


ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 



but i cant find not on Desktop, not in the Home folder  the txt

---

### Post by bayon on 2011-01-06
and i cant mount partition where was the ubuntu. is there something i can do to get my files?

that partition is sda5

---

### Post by mastablasta on 2011-01-06
in windows there is *partition doctor* that fixes corrupted partitions. i am not sure what the linux option is.

---

### Post by bayon on 2011-01-06
SOLVED!!!

1) I booted Slax (*Slax* is a LiveCD Linux distribution)

2) in Disk Manager or Partition Manager (dont know how it called) i find out which sda_ is mine damaged partition, mine was sda**5**

3) and there in Terminal I pasted this (and here you have to write your damadger partition sda number):
```
e2fsck -y -f -v /dev/sda5
```4) rebooted, and Ubuntu was back to normal! Not a file or setting missing! :grin:

---

