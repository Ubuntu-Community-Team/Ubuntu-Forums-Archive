---
title: "Grub slow after Parted used"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by pycoed on 2011-01-12
Hi, I've been running 9.10 on my son's old T41 Thinkpad which originally had XP installed. I set it up with a separate Home partition & an Ubuntu partition, as well as the original XP partition.
Couple of days ago I used Parted to format the XP partition to ext3 & then intended to extend the Ubuntu partition to include it, or keep it as a pure data partition. 
All went well except that when rebooting, I find that Grub takes several minutes to load. |First I get a blank screen with cursor flashing for a few seconds, then "Grub stage 1.5" for a couple of minutes, then "Grub loading" for about 3 minutes, then finally the Grub screen appears & all is well thereafter & loads Ubuntu at normal speed.
How do I get rid of the delays in Grub loading? I have run the bootscript & contents appear below:-
[ATTACH]180807[/ATTACH]

---

### Post by pissedoffdude on 2011-01-12
> **pycoed said:**
> Hi, I've been running 9.10 on my son's old T41 Thinkpad which originally had XP installed. I set it up with a separate Home partition & an Ubuntu partition, as well as the original XP partition.
Couple of days ago I used Parted to format the XP partition to ext3 & then intended to extend the Ubuntu partition to include it, or keep it as a pure data partition. 
All went well except that when rebooting, I find that Grub takes several minutes to load. |First I get a blank screen with cursor flashing for a few seconds, then "Grub stage 1.5" for a couple of minutes, then "Grub loading" for about 3 minutes, then finally the Grub screen appears & all is well thereafter & loads Ubuntu at normal speed.
How do I get rid of the delays in Grub loading? I have run the bootscript & contents appear below:-
[ATTACH]180807[/ATTACH]

Maybe try reinstalling grub?  In a terminal, type ```
sudo fdisk -l
```
Depending on whether your disks are labeled hdaX or sdaX, run
```
sudo grub-install xda
```  where x is replaced by s or h

Afterwards, run a ```
sudo update-grub
```  Reboot and let us know if that works

---

### Post by pycoed on 2011-01-12
Thanks for the response,

"sudo fdisk -l" returns:-

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1467    11783646   83  Linux
/dev/sda2            2238        4864    21101377+   5  Extended
/dev/sda3            1468        2237     6185025   83  Linux
/dev/sda5            2238        2503     2136613+  83  Linux
/dev/sda6            4750        4864      923706   82  Linux swap / Solaris
/dev/sda7            2504        4649    17237713+  83  Linux
/dev/sda8            4650        4749      803218+  82  Linux swap / Solaris

But when I type "sudo grub-install sda" I get "Format of install_device not recognized."?

---

### Post by pissedoffdude on 2011-01-12
> **pycoed said:**
> Thanks for the response,

"sudo fdisk -l" returns:-

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1467    11783646   83  Linux
/dev/sda2            2238        4864    21101377+   5  Extended
/dev/sda3            1468        2237     6185025   83  Linux
/dev/sda5            2238        2503     2136613+  83  Linux
/dev/sda6            4750        4864      923706   82  Linux swap / Solaris
/dev/sda7            2504        4649    17237713+  83  Linux
/dev/sda8            4650        4749      803218+  82  Linux swap / Solaris

But when I type "sudo grub-install sda" I get "Format of install_device not recognized."?

My mistake.  I didn't type the full path, so it should be```
sudo grub-install /dev/sda
```

Try running that, then the second one from my previous post.

---

### Post by pycoed on 2011-01-12
OK thanks - I've tried that & the install command reports no errors:-
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

The update went well too:-

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

However on reboot the behaviour is exactly the same as first reported i.e. very slow to get into the Grub screen, but normal thereafter.

---

