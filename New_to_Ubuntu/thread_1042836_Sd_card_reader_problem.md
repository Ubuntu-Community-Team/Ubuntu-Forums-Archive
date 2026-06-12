---
title: "Sd card reader problem"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Zipper-Shut on 2009-01-18
I've used my SD CARD READER before....
But now, I put an empty brand new 2GB SD card in it and it doesnt sho.w up.
I tried using fdisk -l and it was extremely slow loading the information....
but tis is what i got...

> Disk /dev/sda: 1977 MB, 1977614336 bytes
110 heads, 61 sectors/track, 575 cylinders
Units = cylinders of 6710 * 512 = 3435520 bytes
Disk identifier: 0x0002edb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         576     1931263+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(240, 109, 61) logical=(575, 70, 8)

Disk /dev/sdb: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbb0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         462     3710983+  83  Linux
/dev/sdb2             463         490      224910    5  Extended
/dev/sdb5             463         490      224878+  82  Linux swap / Solaris

Then I tried to mount it... because ive had to do that before with a USB stick.

Then i googled it up about my problem found hardly anything... then ran this code " dmesg | egrep "hd|sd" "

this is what i got:
> [   11.507821] Driver 'sd' needs updating - please use bus_type methods
[   12.373395] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   12.373790] sd 1:0:0:0: [sdb] 7880544 512-byte hardware sectors (4035 MB)
[   12.373833] sd 1:0:0:0: [sdb] Write Protect is off
[   12.373839] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   12.373906] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   12.374060] sd 1:0:0:0: [sdb] 7880544 512-byte hardware sectors (4035 MB)
[   12.374098] sd 1:0:0:0: [sdb] Write Protect is off
[   12.374103] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   12.374168] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   12.374178]  sdb: sdb1 sdb2 < sdb5 >
[   12.376494] sd 1:0:0:0: [sdb] Attached SCSI disk
[   22.897948] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   28.455179] Adding 224868k swap on /dev/sdb5.  Priority:-1 extents:1 across:224868k
[   29.034521] EXT3 FS on sdb1, internal journal
[   30.493850] type=1505 audit(1232252586.735:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4091
[  151.784176] type=1503 audit(1232252708.027:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5694/net/" pid=5694 profile="/usr/sbin/cupsd"
[  152.810580] type=1503 audit(1232252709.051:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5698/net/" pid=5698 profile="/usr/sbin/cupsd"
[  152.811393] type=1503 audit(1232252709.051:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.811970] type=1503 audit(1232252709.051:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.812576] type=1503 audit(1232252709.055:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.815526] type=1503 audit(1232252709.055:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.818486] type=1503 audit(1232252709.059:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.821606] type=1503 audit(1232252709.063:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.824631] type=1503 audit(1232252709.067:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  152.827569] type=1503 audit(1232252709.067:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5698 profile="/usr/sbin/cupsd"
[  154.168767] sd 2:0:0:0: [sda] 3862528 512-byte hardware sectors (1978 MB)
[  154.171771] sd 2:0:0:0: [sda] Write Protect is off
[  154.171784] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[  154.171790] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  154.177769] sd 2:0:0:0: [sda] 3862528 512-byte hardware sectors (1978 MB)
[  154.180777] sd 2:0:0:0: [sda] Write Protect is off
[  154.180793] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[  154.180798] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  154.180812]  sda: sda1
[  334.338750] sd 2:0:0:0: timing out command, waited 180s
[  334.338776] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  334.338785] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[  334.338794] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[  334.338804] end_request: I/O error, dev sda, sector 3862512
[  334.338819] Buffer I/O error on device sda, logical block 482814
[  514.354775] sd 2:0:0:0: timing out command, waited 180s
[  514.354802] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  514.354811] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[  514.354820] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[  514.354831] end_request: I/O error, dev sda, sector 3862512
[  514.354840] Buffer I/O error on device sda, logical block 482814
[  694.561796] sd 2:0:0:0: timing out command, waited 180s
[  694.561823] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  694.561832] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[  694.561841] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[  694.561852] end_request: I/O error, dev sda, sector 3862514
[  694.561862] Buffer I/O error on device sda1, logical block 3862513
[  694.561871] Buffer I/O error on device sda1, logical block 3862514
[  694.561877] Buffer I/O error on device sda1, logical block 3862515
[  694.561884] Buffer I/O error on device sda1, logical block 3862516
[  694.561891] Buffer I/O error on device sda1, logical block 3862517
[  694.561897] Buffer I/O error on device sda1, logical block 3862518
[  694.561904] Buffer I/O error on device sda1, logical block 3862519
[  694.594797] sd 2:0:0:0: timing out command, waited 180s
[  694.594817] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  694.594825] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[  694.594834] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[  694.594845] end_request: I/O error, dev sda, sector 3862512
[  694.594853] Buffer I/O error on device sda, logical block 482814
[  874.610819] sd 2:0:0:0: timing out command, waited 180s
[  874.610845] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  874.610854] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[  874.610863] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[  874.610873] end_request: I/O error, dev sda, sector 3862512
[  874.610882] Buffer I/O error on device sda, logical block 482814
[ 1054.625840] sd 2:0:0:0: timing out command, waited 180s
[ 1054.625867] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1054.625876] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 1054.625885] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[ 1054.625896] end_request: I/O error, dev sda, sector 3862514
[ 1054.625906] Buffer I/O error on device sda1, logical block 3862513
[ 1054.625915] Buffer I/O error on device sda1, logical block 3862514
[ 1054.625922] Buffer I/O error on device sda1, logical block 3862515
[ 1054.625928] Buffer I/O error on device sda1, logical block 3862516
[ 1054.625935] Buffer I/O error on device sda1, logical block 3862517
[ 1054.625941] Buffer I/O error on device sda1, logical block 3862518
[ 1054.625948] Buffer I/O error on device sda1, logical block 3862519
[ 1234.713866] sd 2:0:0:0: timing out command, waited 180s
[ 1234.713894] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1234.713902] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 1234.713912] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[ 1234.713922] end_request: I/O error, dev sda, sector 3862512
[ 1234.713931] Buffer I/O error on device sda, logical block 482814
[ 1414.726891] sd 2:0:0:0: timing out command, waited 180s
[ 1414.726918] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1414.726927] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 1414.726936] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[ 1414.726947] end_request: I/O error, dev sda, sector 3862512
[ 1414.726956] Buffer I/O error on device sda, logical block 482814
pinwyn@pinwyn-laptop:~$ Disk /dev/sda: 1977 MB, 1977614336 bytes
bash: Disk: command not found
pinwyn@pinwyn-laptop:~$ 110 heads, 61 sectors/track, 575 cylinders
bash: 110: command not found
pinwyn@pinwyn-laptop:~$ Units = cylinders of 6710 * 512 = 3435520 bytes
bash: Units: command not found
pinwyn@pinwyn-laptop:~$ Disk identifier: 0x0002edb3
bash: Disk: command not found
pinwyn@pinwyn-laptop:~$ 
pinwyn@pinwyn-laptop:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
pinwyn@pinwyn-laptop:~$ /dev/sda1   *           1         576     1931263+   c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('
pinwyn@pinwyn-laptop:~$ Partition 1 has different physical/logical endings:
bash: Partition: command not found
pinwyn@pinwyn-laptop:~$      phys=(240, 109, 61) logical=(575, 70, 8)
pinwyn@pinwyn-laptop:~$ 
pinwyn@pinwyn-laptop:~$ Disk /dev/sdb: 4034 MB, 4034838528 bytes
bash: Disk: command not found
pinwyn@pinwyn-laptop:~$ 255 heads, 63 sectors/track, 490 cylinders
bash: 255: command not found
pinwyn@pinwyn-laptop:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
pinwyn@pinwyn-laptop:~$ Disk identifier: 0x000cbb0a
bash: Disk: command not found
pinwyn@pinwyn-laptop:~$ 
pinwyn@pinwyn-laptop:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
pinwyn@pinwyn-laptop:~$ /dev/sdb1   *           1         462     3710983+  83  Linux
bash: /dev/sdb1: Permission denied
pinwyn@pinwyn-laptop:~$ /dev/sdb2             463         490      224910    5  Extended
bash: /dev/sdb2: Permission denied
pinwyn@pinwyn-laptop:~$ /dev/sdb5             463         490      224878+  82  Linux swap / Solaris

Now, My computer is a Asus EeePC 900 4GB.
I'm still learning alot of linux stuff... but i do know alot..
If anyone could help me please do.... i really need to use this SD card...

Thank you in advance....:confused:

---

### Post by Zipper-Shut on 2009-02-03
Still need help with this...

is this fixable...

or do i need to buy a new SD CARD READER????


PLEASE HELP!!!!!!!!!!!

---

### Post by sandyd on 2009-02-03
> Disk /dev/sdb: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbb0a

that shows your sd card is detected (2 GB i suppose?)

did you format it?

type this in terminal to format....
```

sudo apt-get install gparted
sudo gparted

```

on the top right hand corner of the window, select /dev/sda

eeeekkk! make sure your formatting the 2GB disk, not the 4GB disk

THEN format it. (and this is what i'm guesssing - you haven't formatted the card)

format it to fat32

P.S. not sure about this one so don't go rushing off to buy another card reader, but some card readers ive encountered in the past do NOT read cards made in Taiwan (even if its not fake)

P.P.S: might think adding recommendation to KDE & Gnome that a "format" function for disks in konqueror and natilus should be added. also might ask for support for unformatted volumes so they show up at least . anyone support that?

---

### Post by aim on 2009-09-08
go to bios and in find a "os installation" option, make it "finished"

---

