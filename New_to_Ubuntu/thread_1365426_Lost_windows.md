---
title: "Lost windows"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by ahajou on 2009-12-27
I have Ubunbtu 9.04 on my machine along with windows XP

A friend of mine removed all the extra kernels from my menu.lst and set windows to default.

After i upgraded my machine, i got a message about the menu.lst file and i chose the restore defaults option.

Now my windows is lost and i dont know how to boot to windows.

I tried downloading KGrubEditor but i couldn't figure out how to add windows from there

---

### Post by muteXe on 2009-12-27
open a terminal and type:

sudo fdisk -l

(that's a small L, not a 1), and paste the output here.  I suspect your windows partition might still be there.

---

### Post by ahajou on 2009-12-27
This is my output:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd2ecd2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81920128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           10200       10442     1951897+   5  Extended
/dev/sda3   *       10443       14593    33342907+  83  Linux
/dev/sda5           10200       10442     1951866   82  Linux swap / Solaris

I m sure my drive is still there, i can read it from the interface, i just cant boot from it

---

### Post by mlentink on 2009-12-27
You say you upgraded. Was this to Ubuntu 9.10?

Do you still see the GRUB menu at start-up? Could you perhaps post the output of 
```
sudo cat /boot/grub/menu.lst
```

---

### Post by wirate on 2009-12-27
if you upgraded to 9.10, open a terminal and

```
sudo update-grub2
```

it will hopefully detect all OS installations

---

### Post by ahajou on 2009-12-27
Thanks guys for the support.

My upgrade was from the upgrade manager in ubuntu 9.04

after downloading the packages it asked to restore the default menu and i accepted.
The new menu now only contain 5 kernels, 2.*.* but the windows is not in the list.

Is there a way I could make grub look for windows and add it to the list?

---

### Post by ElSlunko on 2009-12-27
Reinstalling grub for me works when I encounter this issue. Or try the command in the post above. I think grub-pc or grub2 should work.

---

### Post by ahajou on 2009-12-27
i just tried reinstalling GRUB that didn't work,

Maybe i did not reinstall it right, can u plz write down the script to do so?

Thanks for you concern

---

### Post by kansasnoob on 2009-12-27
Assuming you can boot Ubuntu post the output of these commands:

```
lsb_release -a
```

```
grub-install -v
```

```
cat /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2009-12-27
Oops, left one out:

```
ls /boot/grub
```

---

### Post by kansasnoob on 2009-12-27
> **ahajou said:**
> i just tried reinstalling GRUB that didn't work,

Maybe i did not reinstall it right, can u plz write down the script to do so?

Thanks for you concern

If you can still boot Ubuntu reinstalling grub is not the problem.

---

### Post by ahajou on 2009-12-28
i tried solving this issue by doing a system upgrade
Now my mouse pad is not working and I have no windows, so im left with nothing to work on, please let me know if this can be solved from the live CD:
[http://ubuntuforums.org/showthread.php?p=8571708#post8571708](http://ubuntuforums.org/showthread.php?p=8571708#post8571708)

---

### Post by ahajou on 2009-12-28
lsb_release -a:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
ahmad@Ahmad:~$ grub-install -v
grub-install (GNU GRUB 0.97)





ahmad@Ahmad:~$ cat /boot/grub/menu.lst
default 11
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fc5a7e2b-0529-4c33-978a-dc18d15414b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fc5a7e2b-0529-4c33-978a-dc18d15414b7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		fc5a7e2b-0529-4c33-978a-dc18d15414b7
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fc5a7e2b-0529-4c33-978a-dc18d15414b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		fc5a7e2b-0529-4c33-978a-dc18d15414b7
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=fc5a7e2b-0529-4c33-978a-dc18d15414b7 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
uuid		fc5a7e2b-0529-4c33-978a-dc18d15414b7
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=fc5a7e2b-0529-4c33-978a-dc18d15414b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid		fc5a7e2b-0529-4c33-978a-dc18d15414b7
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=fc5a7e2b-0529-4c33-978a-dc18d15414b7 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, memtest86+
uuid		fc5a7e2b-0529-4c33-978a-dc18d15414b7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,2)
savedefault
makeactive

ahmad@Ahmad:~$ 

The last option I tried to add manually but didn't work.

ahmad@Ahmad:~$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  menu.lst_original  stage1
device.map     grubenv            menu.lst      minix_stage1_5     stage2
e2fs_stage1_5  installed-version  menu.lst~     reiserfs_stage1_5  xfs_stage1_5

---

