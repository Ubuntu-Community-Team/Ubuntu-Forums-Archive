---
title: "samba is changing mount points?"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by ThunderRd on 2008-07-25
I have a dual boot machine with 8.04.1 and XP.  Each OS is on its own IDE drive, XP on the primary.  This machine runs Linux most of the time, and is a file server.  There are also two SATA drives for storage on the machine.  I installed XP first, followed by Ubuntu, and fdisk reported this:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bd87bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6639b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130f286b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a3e006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    b  W95 FAT32
```

As you can see XP is on sda1, Linux on sdb1, and sdc1/sdd1 are the SATA drives.

So far, no problem, although I did wonder at the time why the OS's werent on hda/hdb.  I thought that would be correct for IDE drives.  Anyway, I wanted to set up SAMBA to share some of the directories on the SATA drives with another[XP]machine.  I had all kinds of problems - the drives would show up, then not show up after a reboot/startup; EXTREMELY SLOW copy speeds both to and from the Linux box, (for example the machine wanted 70 minutes to copy a 23MB file to the XP machine); and various other problems with the setup.  I do have some practice with SAMBA in 7.10 but 8.04 has changed all that.

I researched and read inumerable posts over a three day period and decided to start over and set up SAMBA again.  Basically, I installed SAMBA and SMBFS, set the mount points for the two drives in fstab, and slowly worked through smb.conf.

Every time I marked a share, the drive would not automount.  I couldn't understand this but kept looking for the problem.  After some time I realized that the mount points were shifting[?]/changing[?] on their own-like this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x130f286b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a3e006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bd87bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sdc2            1531        4865    26788387+   7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6639b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4660    37431418+  83  Linux
/dev/sdd2            4661        4865     1646662+   5  Extended
/dev/sdd5            4661        4865     1646631   82  Linux swap / Solaris
```

As you can see the output of fdisk is completely different here.  This was giving me fits.  I would get the shares set, the XP box would see them, and could copy them (VERY SLOWLY), but the next time I booted the machine the mount points would disappear and so would the shares - along with the drives not mounting.

I'm not sure what I'm doing wrong.  All I want to do is be able to automount the 2 SATA drives and share some of the directories with the XP machine.  I reckon that something I did wrong was also the cause of the slow file operations.  If I can get SAMBA set up properly, I can check that next.


fstab and smb.conf are here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

UUID=e4e7a3e8-1a47-434d-89b9-27791d79be88 /               ext3    relatime,errors=remount-ro 0       1

UUID=6b80dd2e-1943-4a6b-a432-452160ac8c12 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 	0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 	0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 	0       0

/dev/sdc1	/media/FAT32_REPO	vfat	rw,user,auto,exec	0	0

/dev/sdd1	/media/FAT32_ARCH	vfat	rw,user,auto,exec	0	0
```

```
[global]
    ; General server settings
    netbios name = OPTERON-185
    server string = %h server       (Samba, Ubuntu 8.04.1)
    workgroup = RBZGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = lmhosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
;    path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775

#[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

;[MyFiles]
;    path = /media/samba/
;    browseable = yes
;    read only = no
;    guest ok = no
;    create mask = 0644
;    directory mask = 0755
;    force user = YOUR_USERNAME
;    force group = YOUR_USERGROUP


;My stuff would go here, it isn't there now but will be after I sort this out:
;    path = /media/path/to/share
;    browseable = yes
;    read only = no
;    guest ok = yes

```

---

### Post by DarkMachine on 2008-11-07
I have the same problem, except i have six sata drives in the same computer, every time i reboot, i get the shuffle, so all the samba shares i make are worthless for my media center.  I have yet to find a solution, have you had any sucess? It's very irritating

---

