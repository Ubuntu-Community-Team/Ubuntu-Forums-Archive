---
title: "some issues nautilus / fstab etc"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by ronkas on 2010-10-13
Hi people,
when I open Nautilus (ok)
click on my sda1 partition with Windows 7 on it, Nautilus shows root (ok)
i click random folder, it opens.. (Ok)
but when i click to open "Windows" or Documents and settings ("Users" in W7) or also "Program Data" "Prog data (x86)" etc, it freezes. (grey fading)


I'm trying to understand something of fstab, i also tried pysdm to apply automount at boot, maybe i've done somthing wrong..?
Anyway, here's my fstab

-also when i try to unmount my sda1 or sdb1 it says "na na only root"
-and that funny pysdm when i click on sda1 (left panel) it shows info about sdb5 (swap, totally wrong) 

what a fun eh?




Please help,
i'm really noob to wonderful world of ubuntu!

Thank you in advance and goodnight!




```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb2 :
UUID=aa22fb65-af1e-437f-a250-b2cf9c86c49f    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=C874EF3B74EF2B40    /media/sda1    ntfs-3g    defaults,locale=it_IT.utf8    0    0
#Entry for /dev/sdb1 :
UUID=E2DCC111DCC0E0C1    /media/sdb1    ntfs-3g    defaults,locale=it_IT.utf8    0    0
#Entry for /dev/sdc1 :
UUID=E4322A6F322A4740    /media/sdc1    ntfs-3g    defaults,locale=it_IT.utf8    0    0
#Entry for /dev/sdb5 :
UUID=a5e530c0-7dad-493f-a395-4ff6450ece06    none    swap    sw    0    0


```


and that's my sudo fdisk -l
```
Identificativo disco: 0x0367be40

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           3      620179   312568832    7  HPFS/NTFS

Disco /dev/sdb: 203.9 GB, 203928109056 byte
255 testine, 63 settori/tracce, 24792 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xf77d2833

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       22462   180424991    7  HPFS/NTFS
/dev/sdb2   *       22463       24408    15623168   83  Linux
/dev/sdb3           24408       24793     3096577    5  Esteso
/dev/sdb5           24408       24793     3096576   82  Linux swap / Solaris

```

---

