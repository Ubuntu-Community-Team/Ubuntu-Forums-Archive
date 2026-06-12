---
title: "How to add dvd-rw to capabilities of a DVD+-RW drive?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Ant68 on 2008-12-18
hi,
I am having problems to get my "CD/DVDW TS-H552B" to read and write files from/on a disk "DVD+RW" type. I comfirm [[COLOR="Blue"]_TS-H552B_[/COLOR]]("http://reviews.cnet.com/dvd-drives/samsung-writemaster-ts-h552b/4505-3212_7-31120697.html") hardware has DVD RW capabilities 

Looking at the output below I see in capacity _no mention_ of dvd+rw or dvd-rw or dvd-w. I suspect this is the reason why it is not reading dvd+rw disk when I insert one in the drive and where it does for audio or cd-w.

However, it also does not read  normal video dvd when introducing it in the drive. 

[B]
How can I add to capabilities: dvd-[COLOR="Red"]w[/COLOR] or dvd-[COLOR="Red"]rw[/COLOR] or dvd+[COLOR="Red"][COLOR="Red"]rw[/COLOR][/COLOR] or all to the cdrom1[/B]?

so it looks like: *"capabilities: removable audio cd-r cd-rw dvd dvd-r [COLOR="Red"]dvd-rw[/COLOR]"*

sudo lshw -C disk
...
  *-cdrom:1
       description: DVD writer
       product: CD/DVDW TS-H552B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: TS04
       [COLOR="Red"]capabilities: removable audio cd-r cd-rw dvd dvd-r[/COLOR]
       configuration: ansiversion=5 status=nodisc

[B]etc/fstab:
[/B]proc            /proc           proc    defaults        0       0
UUID=1948d24d-a767-490d-9d69-e513ef76c0ad /               ext3    relatime,errors=remount-ro 0       1
UUID=d19b101d-8f99-4e9f-b78a-07fab9bdd5c1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

**etc/mtab**
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/hemona/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hemona 0 0
/dev/sdb1 /media/OneTouch4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

---

### Post by theamber on 2008-12-18
Did you check for a CDROM Firmware update?
Some drives cannot read certain disks medias.

---

### Post by Ant68 on 2008-12-18
how can I do this? 

Also, I was looking for driver for dvd drive. Does it exist? would it help? (I see stuff for windows not linux).

---

### Post by ProNux on 2008-12-18
> **Ant68 said:**
> how can I do this? 

Also, I was looking for driver for dvd drive. Does it exist? would it help? (I see stuff for windows not linux).

Check out the DVD manufacturer's site, or the OEM if it's an OEM release.  There should be a support section - Firmware updates.  Be careful though, follow instructions carefully in upgrading the firmware; it may damage your DVD Drive.

---

