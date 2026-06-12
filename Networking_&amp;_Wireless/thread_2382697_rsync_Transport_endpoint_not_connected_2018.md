---
title: "rsync Transport endpoint not connected 2018"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by sushi17 on 2018-01-16
Hi All,

trying Windows 10 Ubuntu

created a network share under windows Z:

in bash:

mkdir /mnt/z
sudo mount -t dvrfs Z: /mnt/z

then ran rsync

rsync -arvh /mnt/z/ "mnt/c/Users/Owner/...."

This worked for a while, then I stated getting errors
rsync" link_stat /mnt/z" failed: Transport endpoint is not connected (107)

if I try 

sudo umount /mnt/z

it says the share is busy

any ideas?

---

### Post by TheFu on 2018-01-16
"Did you try turning it off and on again?"
That's my first solution for most things related to Windows.

---

### Post by sushi17 on 2018-01-16
of course, the bash mount was persistent. I tried using lsof and fuser, to see why /mnt/z is busy
 lsof /mnt/z --> Transpoirt endpoint is not connected
mount returns

 mount
rootfs on / type lxfs (rw,noatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,noatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,noatime)
none on /dev type tmpfs (rw,noatime,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,noatime)
none on /run type tmpfs (rw,nosuid,noexec,noatime,mode=755)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,noatime)
none on /run/shm type tmpfs (rw,nosuid,nodev,noatime)
none on /run/user type tmpfs (rw,nosuid,nodev,noexec,noatime,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noatime)
C: on /mnt/c type drvfs (rw,noatime)
Z: on /mnt/z type drvfs (rw,relatime)

---

### Post by sushi17 on 2018-01-16
after searching around

unmount busy device

umount -l ..dev

then remount and works again

---

