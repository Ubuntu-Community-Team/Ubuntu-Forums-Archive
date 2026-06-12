---
title: "Grub missed XP on second drive"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-08-09
I am re-installing my sisters Pc with XP & Ubuntu, but have hit a snag. XP is installed on the second hard drive - SDB1, and I have now installed Ubuntu on SDA1. The problem is that grub did not find the XP install, and I want to know what to add to the menu.lst to enable windows from grub?

---

### Post by SoftwareExplorer on 2009-08-09
would adding something like 

```

title                  WinXP
rootnoverify          (hd1,0)
savedefault
chainloader +1
```to /boot/grub/menu.lst work?

---

### Post by SoftwareExplorer on 2009-08-09
OOPS, double post, sorry!

---

### Post by celticbhoy on 2009-08-09
I tried that, but grub says that there is a disk not found error.
The drive is accessable through Ubuntu.

---

### Post by SoftwareExplorer on 2009-08-09
Maybe if you try different hard drive numbers for the rootnoverify option?
You can edit while your in Grub, IIRC its e to edit, and b to boot when you are ready.

---

### Post by adempewolff on 2009-08-09
This might help: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Scroll down to the bottem of the first post and there is a method that apparently lets "grub recognize your drives".  Might be what you are looking for.

---

### Post by ibuclaw on 2009-08-09
> **celticbhoy said:**
> I tried that, but grub says that there is a disk not found error.
The drive is accessable through Ubuntu.

Firstly, can you post the following:
```
sudo fdisk -lu
```

Secondly:
```
sudo grub
```
And when you enter the **grub>** prompt, type in:
```
find /boot/grub/stage1

```
and that should return your Ubuntu partition in the form (hdX,Y). Copy + Paste that, then type in:
```
quit
```
to leave the grub prompt.

Regards
Iain

---

### Post by celticbhoy on 2009-08-09
> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153565334    76782636   83  Linux
/dev/sda2       153565335   156248189     1341427+   5  Extended
/dev/sda5       153565398   156248189     1341396   82  Linux swap / Solaris

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x044e044d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    80035829    40017883+   7  HPFS/NTFS
jackie@jackie-desktop:~$ jackie
bash: jackie: command not found
jackie@jackie-desktop:~$ 


Ubuntu boot partition is HD0,0

---

### Post by ibuclaw on 2009-08-09
> **celticbhoy said:**
> Ubuntu boot partition is HD0,0

Hmm... and you are sure that the second hard drive has the jumper set to slave?

If not, you could try this workaround:
```

title                  WinXP
rootnoverify          (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1

```
Regards
Iain

---

### Post by celticbhoy on 2009-08-09
thats how i have it set just now, think i might just change the master - slave setup so the windows drive is master and re-install xp.

---

### Post by ibuclaw on 2009-08-09
> **celticbhoy said:**
> thats how i have it set just now, think i might just change the master - slave setup so the windows drive is master and re-install xp.
What is the error you are getting from grub exactly?

Grub always displays an error number to help you diagnose the problem.

Regards
Iain

---

### Post by celticbhoy on 2009-08-09
there is no grub error - it just says there is no drive (cant remember the exact wording) when i select the entry

---

### Post by ibuclaw on 2009-08-09
> **celticbhoy said:**
> there is no grub error - it just says there is no drive (cant remember the exact wording) when i select the entry

hmm... perhaps the disk isn't being recognised at boot time. Just quickly check BIOS to ensure that it is there/detected.

Another test to check if it's being detected properly is when the grub boot menu loads, press **Esc**, then press **c** to drop to the grub shell.

type in
```
geometry (hd0,<TAB>
```
where "<TAB>" is, just press the tab key (usually twice), and you should get a list of filesystems for hd0. 
ie:
> geometry (hd0,<TAB>
Partition num: 0, Filesystem type is ext2fs, partition type 0x83
Partition num: 4, Filesystem type unknown, partition type 0x82

Do the same for hd1
```
geometry (hd1,<TAB>
```
If you get a "Device not recognised" error, then the second hard drive doesn't appear to be being detected by BIOS at bootup.

If it does detect it, make a note of the partition number that XP appears to be on:
ie:
> geometry (**hd1**,<TAB>
Partition num: **0**, Filesystem type unknown, partition type 0x7

Regards
Iain

---

