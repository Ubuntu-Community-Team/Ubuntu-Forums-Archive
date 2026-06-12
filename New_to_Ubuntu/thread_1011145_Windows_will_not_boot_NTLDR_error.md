---
title: "Windows will not boot NTLDR error"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Neon612 on 2008-12-14
This morning I tried booting into Windows XP for the first time after a fresh install of Hardy, NTLDR error, please press ctrl+alt+delete to restart.

The BIOS boot order setup:
160GB - Windows Storage (IDE)
160GB - Windows Boot (SATA)
500GB - Ubuntu Boot/Windows Storage

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

```
sudo fdik -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74207420

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825       19456   125564008+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75706fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       55478   445627003+   7  HPFS/NTFS
/dev/sdb2           55479       60739    42258982+  83  Linux
/dev/sdb3           60740       60801      498015   82  Linux swap / Solaris

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fb91627

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19929   160079661    7  HPFS/NTFS

```

Any and all help will be greatly appreciated, Thank You.

---

### Post by cariboo on 2008-12-14
You may have to use your XP install disk to repair your problem. Boot from the install disk and go into the recovery console and run FIXBOOT and FIXMBR.

Once you have done the above you will have to reinstall grub. You will need to either boot from the LiveCD, or use [this]("http://www.supergrubdisk.org/") to repair grub.

Jim

---

### Post by Neon612 on 2008-12-14
What causes the Windows boot sector to become corrupted?

It worked fine when I had Gutsy installed, but due to an upgrade in the kernal or something my 7.10 install just refused to work so I had to install 8.04 and had a little trouble getting GRUB to find Ubuntu at the time. Windows worked just fine when I installed hardy.

Edit: and from reading around this forum I've looked in the Windows main partition to see if boot.ini, ntldr, and ntldr.com (or something along those lines) were there and they were.

---

### Post by caljohnsmith on 2008-12-14
I think that you are most likely getting the "NTLDR missing" error because you are booting the wrong partition. How about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your existing entry with:
```
title       Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, and let me know exactly what happens when you try each one.

---

### Post by Neon612 on 2008-12-14
The first (hd1) works perfectly, Windows boots like it did before.
The second (hd2) gives me the same error as before.

THank you

PS: If I have Windows installed on sda1 wouldn't that make the root (hd0,0)?
So why do I need to set root to the second hard drive?

---

### Post by caljohnsmith on 2008-12-14
> **Neon612 said:**
> 
PS: If I have Windows installed on sda1 wouldn't that make the root (hd0,0)?
So why do I need to set root to the second hard drive?
sda is only (hd0) when you run Grub commands in Ubuntu. But on start up, (hd0) is simply the first drive in the BIOS boot order, (hd1) is the second boot drive, (hd2) is the third boot drive, etc. So if you boot your Ubuntu sdb drive, that is (hd0), and your other drives would be (hd1) and (hd2). So if using (hd1) works to boot Windows, that means the Windows drive is 2nd in the BIOS boot order.

---

