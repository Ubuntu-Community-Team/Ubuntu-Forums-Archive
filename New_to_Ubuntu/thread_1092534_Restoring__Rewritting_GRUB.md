---
title: "Restoring / Rewritting GRUB"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by PunkLV on 2009-03-10
Greetings. I've installed a fresh copy of Winxp _after_ having Ubuntu install already. Now I can not figure out which partition (and how to find out) should I setup in Grub via *root (hdX.X) setup (hdX)*.
Commandline-way is greatly appriciated. 
How to determine which HDD to use?

I have 3 HDDs:
sda1 - WinXP NTFS
sda2 - ext3 partition
sdb1 - Ubuntu ext3 +swap
sdc1 - ext3 partition

Now, if I select from the BIOS Boot Menu 'sda' WinXP loads w/o showing grub. Even by changing HDD Priority in BIOS I get grub. However, if I do let startup to continue past bootmenu, Grub loads, it has WinXP option, but selecting it grub closes and system frezes trying to boot something.

My grub menu.list:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5564ef02-7d96-4a62-b658-ff5db2a10c06 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5564ef02-7d96-4a62-b658-ff5db2a10c06 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1
```

---

### Post by lobes on 2009-03-10
im a newb so I'll give you my newb solution. First here is the tutorial i used:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

I too coulnt find out which root to use (hdx,x)  so i did an entry for several.  ie:

Title Windows XP
root (hd0,1)
makeactive
chainloader +1

Title Windows XP 2
root (hd0,2)
makeactive
chainloader +1

and so on.  all the way through like 6.  then once the grub menu loads I keep trying untill i found the one that worked then went back and removed the ones that didnt. 

I'm sure there is a better method but it worked for me

EDIT i just saw where u said u had 3 hard drives.  Do you mean three hard drives or three partitions?  if you have three hard drives than (hdX,y) x would represent the hard drive where y would represent the partition i belive.

---

### Post by PunkLV on 2009-03-10
Thanks, yet i did try something like this. Nevertheless, reboot..

---

### Post by PunkLV on 2009-03-10
Nice, now i know that (hd1,0) stores the winxp.. yet root / setup does not help

My helplesness saddens me

Although I am pretty sure theres something missing in menu.lst

---

### Post by presence1960 on 2009-03-10
> **PunkLV said:**
> Greetings. I've installed a fresh copy of Winxp _after_ having Ubuntu install already. Now I can not figure out which partition (and how to find out) should I setup in Grub via *root (hdX.X) setup (hdX)*.
Commandline-way is greatly appriciated. 
How to determine which HDD to use?

I have 3 HDDs:
sda1 - WinXP NTFS
sda2 - ext3 partition
sdb1 - Ubuntu ext3 +swap
sdc1 - ext3 partition

Now, if I select from the BIOS Boot Menu 'sda' WinXP loads w/o showing grub. Even by changing HDD Priority in BIOS I get grub. However, if I do let startup to continue past bootmenu, Grub loads, it has WinXP option, but selecting it grub closes and system frezes trying to boot something.

My grub menu.list:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5564ef02-7d96-4a62-b658-ff5db2a10c06 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5564ef02-7d96-4a62-b658-ff5db2a10c06 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		5564ef02-7d96-4a62-b658-ff5db2a10c06
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1
```

based on what you listed for your HDDs (without seeing your output from sudo fdisk -l), try changing your windows entry in menu.lst to this :

```
title		Windows (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Your Windows is on hd 0 first partition. The first partition on a drive is 0 (zero) in grub.

---

### Post by presence1960 on 2009-03-10
if that doesn't work post the output of > sudo fdisk -l

---

### Post by kansasnoob on 2009-03-10
Ouch! Multiple hard drives wreck my brain!

Consider this a bump!

---

### Post by presence1960 on 2009-03-11
> **kansasnoob said:**
> Ouch! Multiple hard drives wreck my brain!

Consider this a bump!

I know what you mean, but since I have it I had to learn. Thank God for this forum or I would have been lost. I have learned more in here since Sept 2008 than I could have in years with Windows. For that I am grateful.

---

### Post by PunkLV on 2009-03-11
Sorry fro my late reply. Work, etc. Did not try out the *map* method, however

fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6be76be7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19457   125572072+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5d1e5d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19214   154336423+  83  Linux
/dev/sdb2           19215       19457     1951897+   5  Extended
/dev/sdb5           19215       19457     1951866   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641   83  Linux
```

---

### Post by presence1960 on 2009-03-11
> **PunkLV said:**
> Sorry fro my late reply. Work, etc. Did not try out the *map* method, however

fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6be76be7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19457   125572072+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5d1e5d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19214   154336423+  83  Linux
/dev/sdb2           19215       19457     1951897+   5  Extended
/dev/sdb5           19215       19457     1951866   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641   83  Linux
```

Looks like what I posted is correct. Windows is installed on the first hard drive, first partition (hd0,0) in menu.lst. You need the map lines because your windows and ubuntu are on different physical drives (like mine are) I copied that Windows entry right from my menu.lst file and edited it for your set up. Try changing your windows entry in menu.lst to what i suggested and report back.

---

### Post by PunkLV on 2009-03-11
Thanks a bunch. It did work out. However I forgot to mention that I did run *FIXMBR* and *FIXBOOT* from WinxpCD recovery console, so after that, grub prompt at startup would give me the following output for the *uuid* command: 
```
hd0,0 - ext3 my ubuntu
hd1,0 - winxp
```

instead of previous: 
```
hd0,0 - winxp
hd1,0 - ext3 ubuntu
```

so I've used your *map* lines, but edited the *root* to *hd(1,0)* and it had worked! 

Thank you indeed.

Btw, can you please biefly explain what does *map* command does?

---

### Post by presence1960 on 2009-03-11
I do not know exactly what it does. All I know is if your windows partition is on a different physical disk than your Linux it is needed. Maybe someone else can answer that question as I am curious too.

---

### Post by ClaytonOT on 2009-03-11
Your disk matches mine perfectly;

What I did was (and this was literally minutes ago because I just deleted my OpenSUSE so I had to restore my GRUB)

> 
sudo grub
root (hd1,0)
setup (hd0)
quit


I also modified my menu.lst, but not I'm not sure if it's necessary - but if someone can confirm this is a working fix;

> 
title           Ubuntu 8.10, kernel 2.6.27-11-generic
kernel          /boot/vmlinuz-2.6.27-11-generic root=/dev/sdb1 ro
initrd          /boot/initrd.img-2.6.27-11-generic
quiet


I wouldn't implement that change, however until someone comments on it. Works for me, but may not be necessary at all. This was prior to me uninstalling my OpenSUSE and trying to get them to work out - so perhaps just the simple removal of OpenSUSE was what helped me.

Reboot


EDIT: I guess I just saw that you fixed it? :P

---

### Post by PunkLV on 2009-03-11
> Command: map to_drive from_drive

Map the drive from_drive to the drive to_drive. This is necessary when you chain-load some operating systems, such as DOS, if such an OS resides at a non-first drive. Here is an example: 
          grub> map (hd0) (hd1)
          grub> map (hd1) (hd0)
     

The example exchanges the order between the first hard disk and the second hard disk.

So yeah. This actually does the trick.

---

### Post by meierfra. on 2009-03-11
> I do not know exactly what it does. All I know is if your windows partition is on a different physical disk than your Linux it is needed.

Not  quit correct. You need the map line if Windows  is not on the boot drive. So if Windows is  (hd1)  you need the map lines. But if Windows is on (hd0) you do not need the map lines. It does not matter whether Ubuntu and Windows are on the same drive.


> Maybe someone else can answer that question as I am curious too.

The boot sector of a  Windows partition contains instruction to look on  boot drive for the files ntldr (or bootmgr). So if the windows partition is  not on the boot drive,   booting will fail.

As already mentioned in the previous post
  
map (hd0) (hd1)
map (hd1) (hd0)

virtually swaps the first and second hard drive.
So what used to be the second hard drive, will now appear to be the  boot drive, making sure that Window is able to find its boot files.

---

### Post by presence1960 on 2009-03-11
> **meierfra. said:**
> Not  quit correct. You need the map line if Windows  is not on the boot drive. So if Windows is  (hd1)  you need the map lines. But if Windows is on (hd0) you do not need the map lines. It does not matter whether Ubuntu and Windows are on the same drive.




The boot sector of a  Windows partition contains instruction to look on  boot drive for the files ntldr (or bootmgr). So if the windows partition is  not on the boot drive,   booting will fail.

As already mentioned in the previous post
  
map (hd0) (hd1)
map (hd1) (hd0)

virtually swaps the first and second hard drive.
So what use to be the second hard drive, will now appear to be the  boot drive, making sure that Window is able to find its boot files.

Thanks for the explanation. I only knew that it worked but not why it works.

---

