---
title: "would win erase partitions ?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-20
i have win7 and Ubuntu dual booted
if i need to format the win partition, would windows detect the partitions i made using gparted  or would it format the whole hdd ?

---

### Post by daxbau on 2011-04-20
when I used Win7 Ultimate to reinstall win7, it was no problem to select the right partition

a friend told me the basic version could make problems (just give it a try, but don't forget to backup the system and the MBR.)

to backup MBR just run as root
```
dd if=/dev/sda count=1 bs=512 of=/path/to/save/mbr.iso
```
i'd use partimage to make a compressed image of the disks.

---

### Post by deathadder on 2011-04-20
I've had to reinstall Windows 2000 through to Windows 7 on my dualbooting machine, each time I've had the option to tell Windows where to install so you should be fine as long as you don't blindly hit "next".

As with any reinstall the could be problems so make sure you backup your data before you go (both in Windows and Ubuntu) incase something goes wrong! 

The most pain I've had during dual boot reinstalls is getting Grub back so that I can boot into Linux again...which is a faily painless process to give you an idea of what to expect. :D

---

### Post by Mark Phelps on 2011-04-20
> **neil_1 said:**
> i have win7 and Ubuntu dual booted
if i need to format the win partition, would windows detect the partitions i made using gparted  or would it format the whole hdd ?

Depends on HOW you intend to do this.

If you're going to use some kind of Window restore program or recovery media, then it probably WILL erase the entire drive and reformat it.

If you're going to use a partitioning app (e.g., GParted) and do this manually, YOU decide what partitions get reformatted.

---

### Post by neil_1 on 2011-04-20
alright thanks :)
just booted win7 and it detected different partitions :)
not going to install it now :P

---

