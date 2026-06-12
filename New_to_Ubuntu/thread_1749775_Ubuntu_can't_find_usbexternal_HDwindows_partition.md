---
title: "Ubuntu can't find usb/external HD/windows partition"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Faun88 on 2011-05-04
Good day,

When I updated ubuntu to 11.04, ubuntu was unable to detect any inserted USB drives, external HD's or even my windows-partition.

Normally, I have one 250 GB drive, divided in a windows partition and an ubuntu partition.
 
I also have an 1 TB external HD connected. 

After reading on forums and trying alot, I think my /etc/fstab is not correct.

Just some information for easier help:

```
root@HP6830s:/home/dennis# fdisk -l
lege partitie (5) wordt weggelaten

Schijf /dev/sda: 250.1 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x80d2f3ee

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       24019   192932586    7  HPFS/NTFS
/dev/sda2           24020       27981    31824765    7  HPFS/NTFS
/dev/sda3           27982       30402    19433473    5  Uitgebreid
/dev/sda5           27982       30295    18579456   83  Linux

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0xe8900690

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
```Screenshot:

[IMG]http://i.imm.io/5qRb.png[/IMG]

Ps: I used the ubuntu-classic because I don't like unity.

Thanks!

---

### Post by seawolf167 on 2011-05-04
Welcome to the forums!

/etc/fstab allows for filesystems to be mounted automatically upon boot.

To see what is actually mounted, please post the results of 

```
mount
```in between code tags. To see the available partitions, please post the results of

```
sudo fdisk -l
```

---

### Post by Faun88 on 2011-05-04
> **seawolf167 said:**
> Welcome to the forums!

/etc/fstab allows for filesystems to be mounted automatically upon boot.

To see what is actually mounted, please post the results of 

```
mount
```in between code tags. To see the available partitions, please post the results of

```
sudo fdisk -l
```

I have already included the results of fdisk -l in first post.
[B]
Mount:[/B]

> dennis@HP6830s:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/dennis/.Private on /home/dennis type ecryptfs (ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=6d26c7a1b4140a19,ecryptfs_fnek_sig=039f826f24d669d3)
gvfs-fuse-daemon on /home/dennis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dennis)


---

### Post by Faun88 on 2011-05-04
Somehow, I managed to fix it using this [thread]("http://ubuntuforums.org/showthread.php?t=785263"). Great! :popcorn:

---

### Post by seawolf167 on 2011-05-04
Looks like all you have mounted is /sda5 (your linux system)

you can manually mount the others with

```
mkdir /path/to/mounted/drive
mount /dev/sda1 /path/to/mounted/drive
```

where you will want to mount the below bolded items to have access to all your NTFS partitions

```
 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
**/dev/sda1**   *           1       24019   192932586    7  HPFS/NTFS
**/dev/sda2**           24020       27981    31824765    7  HPFS/NTFS
**/dev/sda3 **          27982       30402    19433473    5  Uitgebreid
/dev/sda5           27982       30295    18579456   83  Linux

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0xe8900690

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
**/dev/sdb1  **             1      121601   976760001    7  HPFS/NTFS
```

---

