---
title: "aoe: unknown cmd 240 in syslog"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by karaluh on 2008-10-18
I'm trying to configure network backup through aoe on Welland ME-747K-SI. The problemem is that the drive isn't mounted during system startup. Manual mount works fine.
 
 /etc/fstab:
 /dev/etherd/e0.0 /mnt/backup/ ext3 relatime 0 0
 
The first thing, that cought my attention is a lot of
 
 aoe: unknown cmd 240
 
errors in syslog. Google doesn't give any info on the subject. Any ideas?

---

### Post by cariboo on 2008-10-18
What is the output of cat /etc/mtab when your device is mounted?

Jim

---

### Post by karaluh on 2008-10-18
> **cariboo907 said:**
> What is the output of cat /etc/mtab when your device is mounted?


/dev/md1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
/dev/md0 /boot ext3 rw,relatime 0 0
/dev/md2 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/etherd/e0.0 /mnt/backup ext3 rw,relatime 0 0

---

