---
title: "Please HELP, Grub stole my boot drive!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by bamim2 on 2011-01-27
I have Windoze XP installed on one hard drive & installed Ubuntu 10.10 on another hard drive; making it a dual boot system. I can boot to either system fine. 

I cloned my WinXP drive & when it's in the system without the Ubuntu drive, boots up I'm getting the Grub message: 

```

```error: no such device:10ddaf38-xxxxx-xxx-xxx-xxxx. 
grub rescue>_```

```

It appears that Grub has stolen my Windoze boot drive. Does anyone know how I can fix that? Can I remove Grub from the Windoze drive or something or can I turn it off while I clone the other drive?

---

### Post by drs305 on 2011-01-27
If you want to restore the Windows bootloader, you can redirect the MBR to point to the partition with the boot flag (Windows partition) by running the following commands from the Ubuntu installation/LiveCD. 

Make sure to change "sda" if the drive identified as "sda" is not the one you want to change:

```
sudo apt-get install lilo
sudo lilo -M /dev/**sda** mbr
```
Run only those two commands. Disregard messages about lilo not being fully installed.

---

### Post by bamim2 on 2011-01-27
Wow, THANK YOU for this. Let me make sure I understand this before I start. 

Does Ubuntu have a default root password (since I'm doing the "sudo" command)? 

Do you suggest I put the drives back the way they were (remove the cloned hard drive), then point the MBR back to the Windows hard drive, then clone the drive again?

Should I use GParted to see the partitions or something? What am I actually looking for exactly? How would I know if "sda" is or isn't the drive I want to change?

Sorry, but I'm pretty much a  NUBEE & I've shot myself in the foot with grub & lilo before & made my drive unbootable & unrecoverable (at least by me). If you could just give me a little more clarification on this I would feel much more comfortable.

---

### Post by drs305 on 2011-01-27
You can run "sudo fdisk -l" (that's a lowercase L) and it should display both drives. The one with Ubuntu will have a partition "Linux" and probably one called "swap / Solaris". It will also have NTFS partitions. 

You can also use Gparted to see them (System, Administration, Gparted/Partition Editor).

With either of the above, check that the Windows partition has the 'boot' flag (it's an asterisk in the "fdisk" output or you can check the flag column in Gparted.

The cloned drive, if it has only Windows on it, won't have any Linux partitions.

On a LiveCD, you use "sudo" but there is no password necessary.

If you cloned your partitions, you might want to change the UUID of the cloned partition(s). Having the same UUID on both drives' partitions is going to confuse Linux. You can change the UUID of the Windows clone partition (and any other cloned partitions) with the following command:
```
sudo tune2fs -U random /dev/sd**aX**
```
with **aX** being the Windows clone partition number (Example: sudo tune2fs -U random /dev/sd**a1**).

---

### Post by bamim2 on 2011-01-27
I got it!!! THANK YOU for staying with me on this & helping me out. I greatly appreciate it!

---

