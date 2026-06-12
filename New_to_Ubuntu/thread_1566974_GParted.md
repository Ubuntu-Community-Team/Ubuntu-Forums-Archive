---
title: "GParted"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by chong601 on 2010-09-03
Hey guys,

I'd like to ask that is GParted able to reset MBR?

---

### Post by garvinrick4 on 2010-09-03
You can use a Live CD and with a few commands reinstall grub to mbr
If you need help can give you the commands. Must have a ubuntu install CD
which is your Live CD. If you do not have one download and then BURN to CD as slow
as program will allow.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Mark Phelps on 2010-09-03
> **chong601 said:**
> Hey guys,

I'd like to ask that is GParted able to reset MBR?

For which kind of filesystem drive -- Linux? or MS Windows?

---

### Post by garvinrick4 on 2010-09-03
> **Mark Phelps said:**
> For which kind of filesystem drive -- Linux? or MS Windows? Good question just assumed Linux Grub, should not assume.

---

### Post by techningeer on 2010-09-03
GParted cannot change the MBR. You must configure the bootloader appropriately, then run the bootloader config command. Sometimes running 'grub-configurator' as root can do the job.

---

### Post by srs5694 on 2010-09-03
The question is ambiguous, and the responses are all making assumptions about the meaning of the question. The Master Boot Record (MBR) is a data structure that resides in the first sector of most hard disks. It contains two important types of information, which are manipulated using two different types of utilities:


[list]
[*]**The MBR partition table** -- This is a description of the first four partitions on the disk (/dev/sda1 through /dev/sda4, for the first Linux disk). Tools such as GNU Parted, GParted, and fdisk manipulate the MBR partition table, and can re-write it.
[*]**The stage 0 boot loader** -- This is the first disk-based code that the BIOS reads when booting the computer. On an Ubuntu system, it's normally the GRUB Legacy or GRUB 2 code, which is installed via tools like "grub-install".
[/list]


Chong601, I suggest you clarify your question. What precisely do you want to do, and why? If your system isn't booting or you want to change the boot loader, then you'll need to reconfigure your boot loader, but precisely how depends on the nature of the problem. If your partition table is corrupt, then you'll need to fix it with a partitioning tool such as GParted or fdisk -- but precisely how depends on the nature of the problem.

---

