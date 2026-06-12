---
title: "question about mtab, fstab, external hard drives, and this 'read only' nonsense...."
date: 2009-07-16
forum: New to Ubuntu
---

### Post by earthpigg on 2009-07-16
is there a way to simply tell ubuntu:

"stop trying to be smarter than me. any time i plug *any* external media in that my system is *physically capable* of reading/writing from/to and deleting, _*mount it as such!*_"

anyways, same problem that seems to happen all the time all over the forums, but that seems to have no reliable fix:

external usb hard drive, fat32, magically and suddenly unable to reliably read/write to it, empty the trash, etc. sudo nautilus does not fix this. essentially i just mount and unmount it a bunch till it briefly plays nice. i have run fsck.msdos on the drive.

cat /etc/fstab and /etc/mtab:
```

**ep@ep-9:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=d2ebb592-5cae-415b-9962-40821c530f09 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=9e58ee8d-fc24-4375-967a-d66345b52542 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=a80cade5-f107-41b5-08a7-bcef9ff5a5a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
**ep@ep-9:~$ cat /etc/mtab**
/dev/sda2 / ext4 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-14-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda1 /home ext4 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ep/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ep 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
ep@ep-9:~$ 

```


/dev/sdb1 aka /media/disk is the external hard drive.

---

### Post by mcduck on 2009-07-16
Actually your drive is mounted with correct permissions for both read and write. Since you lost the ability suddenly I'd assume that this is because of some hardware/filesystem error on that device, as the default policy in case of errors is to remount the drive as read-only to prevent data loss.

I suggest checking through your system logs to see if there are any I/O errors for that drive. And if there are, your drive (or filesystem on the drive) is failing.

---

### Post by earthpigg on 2009-07-16
in /var/log/btmp

```
Jul 16 18:13:12 ep-9 kernel: [152013.089544] sd 8:0:0:0: Attached scsi generic sg2 type 0
Jul 16 18:13:13 ep-9 hald: mounted /dev/sdb1 on behalf of uid 1000
Jul 16 18:14:04 ep-9 kernel: [152065.068014] FAT: Filesystem panic (dev sdb1)
Jul 16 18:14:04 ep-9 kernel: [152065.068023]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jul 16 18:14:04 ep-9 kernel: [152065.068031]     File system has been set read-only
```

indicates my external hard drive (/dev/sdb) is failing?

:(

---

### Post by earthpigg on 2009-07-16
i know this is random, but could this somehow be related to ubuntu one??

looking back through the logs, and comparing that to what i remember of what i was doing:

i was backing up my /home using nautilus, accidentally included the "~/Ubuntu One" directory in that, saw what i did, hit cancel...

```
Jul 16 16:38:07 ep-9 kernel: [146307.784207] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jul 16 16:38:07 ep-9 kernel: [146307.927907] usb 1-4: configuration #1 chosen from 1 choice
Jul 16 16:38:07 ep-9 kernel: [146307.928522] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 16 16:38:07 ep-9 kernel: [146307.928991] usb-storage: device found at 4
Jul 16 16:38:07 ep-9 kernel: [146307.928995] usb-storage: waiting for device to settle before scanning
Jul 16 16:38:12 ep-9 kernel: [146312.924612] usb-storage: device scan complete
Jul 16 16:38:12 ep-9 kernel: [146312.925288] scsi 6:0:0:0: Direct-Access     WD       3200BEV External 1.05 PQ: 0 ANSI: 4
Jul 16 16:38:12 ep-9 kernel: [146312.927356] sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Jul 16 16:38:12 ep-9 kernel: [146312.929202] sd 6:0:0:0: [sdb] Write Protect is off
Jul 16 16:38:12 ep-9 kernel: [146312.929208] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
Jul 16 16:38:12 ep-9 kernel: [146312.929213] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jul 16 16:38:12 ep-9 kernel: [146312.929948] sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Jul 16 16:38:12 ep-9 kernel: [146312.935716] sd 6:0:0:0: [sdb] Write Protect is off
Jul 16 16:38:12 ep-9 kernel: [146312.935723] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
Jul 16 16:38:12 ep-9 kernel: [146312.935728] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jul 16 16:38:12 ep-9 kernel: [146312.935737]  sdb: sdb1 sdb2
Jul 16 16:38:12 ep-9 kernel: [146312.982097] sd 6:0:0:0: [sdb] Attached SCSI disk
Jul 16 16:38:12 ep-9 kernel: [146312.982235] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jul 16 16:39:18 ep-9 hald: mounted /dev/sdb1 on behalf of uid 1000
Jul 16 16:39:33 ep-9 kernel: [146393.830142] nautilus[24020]: segfault at 8 ip 00007f423a1805ea sp 00007fff54641bc0 error 4 in libnautilus-ubuntuone.so[7f423a17d000+5000]
Jul 16 16:40:01 ep-9 /USR/SBIN/CRON[24087]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul 16 16:43:26 ep-9 dhclient: DHCPREQUEST of 192.168.0.6 on wlan0 to 192.168.0.1 port 67
Jul 16 16:43:27 ep-9 dhclient: DHCPACK of 192.168.0.6 from 192.168.0.1
Jul 16 16:43:27 ep-9 dhclient: bound to 192.168.0.6 -- renewal in 1439 seconds.
Jul 16 16:45:01 ep-9 /USR/SBIN/CRON[24433]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul 16 16:50:02 ep-9 /USR/SBIN/CRON[24555]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul 16 16:50:14 ep-9 ntpd[7987]: kernel time sync status change 0001
Jul 16 16:55:02 ep-9 /USR/SBIN/CRON[24840]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul 16 17:00:01 ep-9 /USR/SBIN/CRON[24995]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jul 16 17:00:01 ep-9 /USR/SBIN/CRON[24997]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul 16 17:05:02 ep-9 /USR/SBIN/CRON[25404]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul 16 17:07:26 ep-9 dhclient: DHCPREQUEST of 192.168.0.6 on wlan0 to 192.168.0.1 port 67
Jul 16 17:07:27 ep-9 dhclient: DHCPACK of 192.168.0.6 from 192.168.0.1
Jul 16 17:07:27 ep-9 dhclient: bound to 192.168.0.6 -- renewal in 1673 seconds.
Jul 16 17:10:01 ep-9 /USR/SBIN/CRON[25569]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul 16 17:15:02 ep-9 /USR/SBIN/CRON[25895]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul 16 17:15:47 ep-9 kernel: [148567.427738] FAT: Filesystem panic (dev sdb1)
Jul 16 17:15:47 ep-9 kernel: [148567.427743]     fat_free_clusters: deleting FAT entry beyond EOF
Jul 16 17:15:47 ep-9 kernel: [148567.427746]     File system has been set read-only
Jul 16 17:17:01 ep-9 /USR/SBIN/CRON[26062]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 17:19:05 ep-9 hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Jul 16 17:19:09 ep-9 hald: mounted /dev/sdb1 on behalf of uid 1000
Jul 16 17:19:26 ep-9 kernel: [148786.587247] FAT: Filesystem panic (dev sdb1)
Jul 16 17:19:26 ep-9 kernel: [148786.587256]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jul 16 17:19:26 ep-9 kernel: [148786.587264]     File system has been set read-only
Jul 16 17:20:01 ep-9 /USR/SBIN/CRON[26251]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul 16 17:20:50 ep-9 kernel: [148870.419449] FAT: Filesystem panic (dev sdb1)
Jul 16 17:20:50 ep-9 kernel: [148870.419453]     fat_get_cluster: invalid cluster chain (i_pos 0)
Jul 16 17:21:07 ep-9 kernel: [148887.523442] FAT: Filesystem panic (dev sdb1)
Jul 16 17:21:07 ep-9 kernel: [148887.523446]     fat_get_cluster: invalid cluster chain (i_pos 0)
```

note that one of the last log entries prior to the first FAT filesystem panic involves ubuntu one.

---

### Post by earthpigg on 2009-07-16
plugged it into a second computer, also running ubuntu 9.04.

worked without a hitch. not a single out-of-place entry in syslog on that computer.

manually deleted .Trash-1000. deleted a file. emptied the trash.

created a file 'testt'. unmounted and removed the usb drive from computer #2 and back into computer #1, where i had been having issues in the past.

not a single odd syslog entry.

was able to delete the file 'testt' and empty the trash without a hitch.

copying over 39.2 gigs of data right now.

after, will try to recreate the odd behaviour with the ubuntu one directory and if i start having the same exact issues caused by the exact same thing again, i will submit a bug report.


do you (or others) have any suggested information that i should include in the bug report, aside from what is included in this thread already (i will probably just briefly describe the problem and link to this thread)?

---

### Post by mcduck on 2009-07-16
Hitting cancel in Nautilus definitely shouldn't cause filesystem panic, but since the log says that Nautilus segfaulted it sure is possible that something went wrong and caused filesystem errors. Based on this I'd say the problem is more likelty resulting from this segfault than from the actual drive itself being broken.

I would have suggested running fsck on the drive, but you said you have already done that and I don't really trust fscking Windows file systems anyway. If you have the possibility, you could try checking the filesystem on some Windows machine, perhaps that would be able to repair the filesystem if fsck didn't do it.

If that's not possible or doesn't help you should backup the data from that drive to somewhere else and reformat the drive.

(Also if you want to be absolutely sure that it's not hardware problem you could try some SMART tool for checking the drives status. But the nautilus segfault does seem to be the most likely reason for your problem)

edit: Great, you got it solved already. If you end writing a bug report then explaining what you were doing and attaching that log should be enough. But of course you should read the bug reporting instructions in Launchpad as well.. :)

---

### Post by earthpigg on 2009-07-16
> **mcduck said:**
> 
edit: Great, you got it solved already. 

yup, thanks for the help! :D

---

