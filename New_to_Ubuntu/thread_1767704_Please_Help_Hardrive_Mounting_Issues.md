---
title: "Please Help Hardrive Mounting Issues"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by eddiekoski on 2011-05-26
Short Story: I am running Ubuntu off a thumb drive I was able to mount and external usb 3tb volume and used the FTP client  filezilla to transfer files to my windows 7 computer and it was working, but ever since I unplugged it it wont mount , it is detected but wont mount.

Long story (Feel free to skip this ): I had a windows 7 ultimate 64 bit installed on my desktop on raid 10 (0+1)
with almost 2 TB of data. I used a GParted Live CD to copy entire drive to my external 3TB Hitachi hard drive in order to change my raid and copy back the files from the external hard drive. However GParted no longer recognized the NTFS partition windows does not recognize the NTFS partition it comes up as RAW however by some luck Ubuntu recognizes it and all my system files and programs are there and I copied most of them over to a blank NTFS partition on WIndows 7 through the network using the FTP client Filezilla however I was not able to finish because everyone in a while the external drives slows down and I unpluged it then repluged it then it would go full speed again and I would continue filezilla then one day it just would not mount. The three partions I have on it are detected however they wont mount. I did this same process with my laptop I coppied my laptop hardrive to an external drive using GPARTED then I put the external drive in used startup repar for windows 7 it booted so it may be related to the raid.?

Here is the message When I plug in the external hardrive:
Unable to mount 1.9 TB Filesystem
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

How can I make Ubuntu mount the drive? I think it thinks that a old session of Ubuntu has a lock on it still.

---

### Post by fdrake on 2011-05-26
> **eddiekoski said:**
>  Ubuntu recognizes it and all my system files and programs are there and I copied most of them over to a blank NTFS partition on WIndows 7 through the network using the FTP client Filezilla however 

i am confused??!!! what's exactly the scenario?
1 pc ?or 2 pc connected with a network?

---

### Post by eddiekoski on 2011-05-26
2 pc's a laptop and a desktop the overall problem is that I cannot mount my external hardrive anymore and it use to mount perfectly. This is on my laptop with Ubuntu.

---

### Post by fdrake on 2011-05-26
can u paste here the outputs of these comnds(1 by 1) with the usb disk plugged in:
```
less /etc/fstab
mount
ls -al /dev
```v

---

### Post by eddiekoski on 2011-05-26
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/etc/fstab (END) 
  
thats the output for the first command it has been like that for more thanseveral  hours  and has not finished.

By the way I am expecting to get asked the drives location at some point so I will tell you know
/dev/sdd
then the three partitions are
/dev/sdd1
/dev/sdd2 (this is the main one I wan to get mounted again)
/dev/sdd3

---

### Post by fdrake on 2011-05-26
> **eddiekoski said:**
> aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/etc/fstab (END) 
  
thats the output for the first command it has been like that for more thanseveral  hours  and has not finished.

By the way I am expecting to get asked the drives location at some point so I will tell you know
/dev/sdd
then the three partitions are
/dev/sdd1
/dev/sdd2 (this is the main one I wan to get mounted again)
/dev/sdd3
what about the mount list? to see if ti is already mounted..
```
mount
```

---

### Post by eddiekoski on 2011-05-26
ubuntu@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1536344k,nr_inodes=211402,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=f016e2be)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdc1 on /media/89F5-60AE__ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
/dev/sdd1 on /media/89F5-60AE___ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
ubuntu@ubuntu:~$ sudo mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1536344k,nr_inodes=211402,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=f016e2be)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdc1 on /media/89F5-60AE__ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
/dev/sdd1 on /media/89F5-60AE___ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
ubuntu@ubuntu:~$ 

I rand it again as sudo because it mentioned root

---

### Post by eddiekoski on 2011-05-26
> **fdrake said:**
> what about the mount list? to see if ti is already mounted..
```
mount
```

I did the mount command see my reply please

---

### Post by fdrake on 2011-05-27
the partition u refear doesn't even show up, that's not gooodd....
let's try to see if fuser can help us out

```

fuser -m /dev/sdd2
<output of process PID>
ps --pid <process PID number>
<output of the program>

```

if fuser doesn't show any program I am afraid i am out of ideas theN...

good luck!

---

### Post by eddiekoski on 2011-05-27
ubuntu@ubuntu:~$ fuser -m /dev/sdd2
Specified filename /dev/sdd2 does not exist.
Cannot stat file /proc/4191/fd/21: Stale NFS file handle
Cannot stat file /proc/4191/fd/22: Stale NFS file handle
ubuntu@ubuntu:~$ fuser -m /dev/sde2
Cannot stat file /proc/4191/fd/21: Stale NFS file handle
Cannot stat file /proc/4191/fd/22: Stale NFS file handle
ubuntu@ubuntu:~$ <out of process PID>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$ ps --pid 
ERROR: List of process IDs must follow --pid.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
ubuntu@ubuntu:~$ ps --pid 4191
  PID TTY          TIME CMD
 4191 ?        00:00:14 nautilus
ubuntu@ubuntu:~$ nautilus
ubuntu@ubuntu:~$ 

looks like letter god change to sde2 so I adjusted the commands it looks like nautilus is the program involved interfering with the mount I think it is like ubuntu's equivalent to windows explorer I am now confused?

---

### Post by eddiekoski on 2011-05-27
Also one of the partitions is showing up 3 times on desktop it is the same partition 3 times and wont unmount because it says it is not mounted and wont open,

---

### Post by fdrake on 2011-05-27
u said u used that partition to share file on the network right? well nfs is a "network file system" currently working.

try this hope it works:

```

kill -9 4191
exportfs -f
mount -o remount /dev/sdd2 (or sde2?)

```

---

### Post by eddiekoski on 2011-05-27
ubuntu@ubuntu:~$ kill -9 4191
ubuntu@ubuntu:~$ exportfs -f
The program 'exportfs' is currently not installed.  You can install it by typing:
sudo apt-get install nfs-kernel-server
ubuntu@ubuntu:~$ mount -o remount /dev/sde2
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sde2
mount: can't find /dev/sde2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sdd2
mount: can't find /dev/sdd2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sde2
mount: can't find /dev/sde2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sdf2
mount: can't find /dev/sdf2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sdf
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount -o remount /dev/sdf2
mount: can't find /dev/sdf2 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo apt-get install nfs-kernel-server
Reading package lists... Error!
E: Could not open file /var/lib/apt/lists/Ubuntu%2011.04%20%5fNatty%20Narwhal%5f%20-%20Release%20i386%20(20110427.1)_dists_natty_Release - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ :
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ :sudo apt-get install nfs-kernel-server
No command ':sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
:sudo: command not found

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ fuser -m /dev/sdf2
ubuntu@ubuntu:~$ sudo fuser -m /dev/sdf2
ubuntu@ubuntu:~$ sudo fuser -m /dev/sde2
Specified filename /dev/sde2 does not exist.
ubuntu@ubuntu:~$ sudo fuser -m /dev/sdf2
ubuntu@ubuntu:~$ 

Thats what I did I do not understand the ubuntu command line that well...
The actual harddrive started blinking its light and stuff but it still wont mount.

---

### Post by eddiekoski on 2011-05-29
I ran the commands again it looks like they gave more interesting output
ubuntu@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1536344k,nr_inodes=211402,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=ae918a82)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdc1 on /media/V0____ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
/dev/sdd1 on /media/V0_____ type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
ubuntu@ubuntu:~$ ls -al /dev
total 4
drwxr-xr-x  19 root   root        4420 2011-05-29 04:41 .
drwxrwxrwx  34 root   root        4096 2011-05-29 00:30 ..
crw-rw----   1 root   video    10, 175 2011-05-29 00:30 agpgart
crw-------   1 root   root     10, 235 2011-05-29 00:30 autofs
drwxr-xr-x   2 root   root         800 2011-05-29 04:41 block
drwxr-xr-x   2 root   root         120 2011-05-29 04:41 bsg
crw-------   1 root   root     10, 234 2011-05-29 00:30 btrfs-control
drwxr-xr-x   3 root   root          60 2011-05-29 00:30 bus
lrwxrwxrwx   1 root   root           3 2011-05-29 00:30 cdrom -> sr0
lrwxrwxrwx   1 root   root           3 2011-05-29 00:30 cdrw -> sr0
drwxr-xr-x   2 root   root        3800 2011-05-29 04:41 char
crw-------   1 root   root      5,   1 2011-05-29 00:30 console
lrwxrwxrwx   1 root   root          11 2011-05-29 00:30 core -> /proc/kcore
drwxr-xr-x   2 root   root          60 2011-05-29 00:30 cpu
crw-------   1 root   root     10,  59 2011-05-29 00:30 cpu_dma_latency
drwxr-xr-x   6 root   root         120 2011-05-29 00:30 disk
drwxr-xr-x   2 root   root          80 2011-05-29 00:30 dri
lrwxrwxrwx   1 root   root           3 2011-05-29 00:30 dvd -> sr0
lrwxrwxrwx   1 root   root           3 2011-05-29 00:30 dvdrw -> sr0
crw-------   1 root   root     10,  61 2011-05-29 00:30 ecryptfs
crw-rw----   1 root   video    29,   0 2011-05-29 00:30 fb0
lrwxrwxrwx   1 root   root          13 2011-05-29 00:30 fd -> /proc/self/fd
crw-rw-rw-   1 root   root      1,   7 2011-05-29 00:30 full
crw-rw-rw-   1 root   fuse     10, 229 2011-05-29 00:30 fuse
crw-------   1 root   root    251,   0 2011-05-29 00:30 fw0
crw-------   1 root   root     10, 228 2011-05-29 00:30 hpet
drwxr-xr-x   3 root   root          60 2011-05-29 00:30 .initramfs
-rw-r--r--   1 root   root           0 2011-05-29 00:30 .initramfs-tools
drwxr-xr-x   3 root   root         240 2011-05-29 00:30 input
crw-------   1 root   root      1,  11 2011-05-29 00:30 kmsg
srw-rw-rw-   1 root   root           0 2011-05-29 00:30 log
brw-rw----   1 root   disk      7,   0 2011-05-29 00:30 loop0
brw-rw----   1 root   disk      7,   1 2011-05-29 00:30 loop1
brw-rw----   1 root   disk      7,   2 2011-05-29 00:30 loop2
brw-rw----   1 root   disk      7,   3 2011-05-29 00:30 loop3
brw-rw----   1 root   disk      7,   4 2011-05-29 00:30 loop4
brw-rw----   1 root   disk      7,   5 2011-05-29 00:30 loop5
brw-rw----   1 root   disk      7,   6 2011-05-29 00:30 loop6
brw-rw----   1 root   disk      7,   7 2011-05-29 00:30 loop7
drwxr-xr-x   2 root   root          60 2011-05-29 00:30 mapper
crw-------   1 root   root     10, 227 2011-05-29 00:30 mcelog
crw-r-----   1 root   kmem      1,   1 2011-05-29 00:30 mem
drwxr-xr-x   2 root   root          60 2011-04-25 22:51 net
crw-------   1 root   root     10,  58 2011-05-29 00:30 network_latency
crw-------   1 root   root     10,  57 2011-05-29 00:30 network_throughput
crw-rw-rw-   1 root   root      1,   3 2011-05-29 00:30 null
crw-------   1 root   root      1,  12 2011-05-29 00:30 oldmem
drwxr-xr-x   2 root   root          60 2011-05-29 00:30 pktcdvd
crw-r-----   1 root   kmem      1,   4 2011-05-29 00:30 port
crw-------   1 root   root    108,   0 2011-05-29 00:30 ppp
crw-------   1 root   root     10,   1 2011-05-29 00:30 psaux
crw-rw-rw-   1 root   tty       5,   2 2011-05-29 04:42 ptmx
drwxr-xr-x   2 root   root           0 2011-04-07 12:43 pts
brw-rw----   1 root   disk      1,   0 2011-05-29 00:30 ram0
brw-rw----   1 root   disk      1,   1 2011-05-29 00:30 ram1
brw-rw----   1 root   disk      1,  10 2011-05-29 00:30 ram10
brw-rw----   1 root   disk      1,  11 2011-05-29 00:30 ram11
brw-rw----   1 root   disk      1,  12 2011-05-29 00:30 ram12
brw-rw----   1 root   disk      1,  13 2011-05-29 00:30 ram13
brw-rw----   1 root   disk      1,  14 2011-05-29 00:30 ram14
brw-rw----   1 root   disk      1,  15 2011-05-29 00:30 ram15
brw-rw----   1 root   disk      1,   2 2011-05-29 00:30 ram2
brw-rw----   1 root   disk      1,   3 2011-05-29 00:30 ram3
brw-rw----   1 root   disk      1,   4 2011-05-29 00:30 ram4
brw-rw----   1 root   disk      1,   5 2011-05-29 00:30 ram5
brw-rw----   1 root   disk      1,   6 2011-05-29 00:30 ram6
brw-rw----   1 root   disk      1,   7 2011-05-29 00:30 ram7
brw-rw----   1 root   disk      1,   8 2011-05-29 00:30 ram8
brw-rw----   1 root   disk      1,   9 2011-05-29 00:30 ram9
crw-rw-rw-   1 root   root      1,   8 2011-05-29 00:30 random
crw-rw-r--+  1 root   root     10,  62 2011-05-29 00:30 rfkill
lrwxrwxrwx   1 root   root           4 2011-05-29 00:30 rtc -> rtc0
crw-------   1 root   root    254,   0 2011-05-29 00:30 rtc0
lrwxrwxrwx   1 root   root           3 2011-05-29 00:30 scd0 -> sr0
brw-rw----   1 root   disk      8,   0 2011-05-29 00:30 sda
brw-rw----   1 root   disk      8,   1 2011-05-29 00:30 sda1
brw-rw----   1 root   disk      8,   2 2011-05-29 00:30 sda2
brw-rw----   1 root   disk      8,  16 2011-05-29 00:30 sdb
brw-rw----   1 root   disk      8,  17 2011-05-29 00:30 sdb1
brw-rw----   1 root   disk      8,  48 2011-05-29 04:41 sdd
brw-rw----   1 root   disk      8,  49 2011-05-29 04:41 sdd1
brw-rw----   1 root   disk      8,  50 2011-05-29 04:41 sdd2
brw-rw----   1 root   disk      8,  51 2011-05-29 04:41 sdd3
crw-rw----   1 root   disk     21,   0 2011-05-29 00:30 sg0
crw-rw----+  1 root   cdrom    21,   1 2011-05-29 00:30 sg1
crw-rw----   1 root   disk     21,   2 2011-05-29 00:30 sg2
crw-rw----   1 root   disk     21,   3 2011-05-29 04:41 sg3
drwxrwxrwt   2 root   root         140 2011-05-29 04:42 shm
crw-------   1 root   root     10, 231 2011-05-29 00:30 snapshot
drwxr-xr-x   3 root   root         180 2011-05-29 00:30 snd
brw-rw----+  1 root   cdrom    11,   0 2011-05-29 00:30 sr0
lrwxrwxrwx   1 root   root          15 2011-05-29 00:30 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root   root          15 2011-05-29 00:30 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root   root          15 2011-05-29 00:30 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root   tty       5,   0 2011-05-29 00:30 tty
crw--w----   1 root   tty       4,   0 2011-05-29 00:30 tty0
crw-------   1 ubuntu tty       4,   1 2011-05-29 00:30 tty1
crw--w----   1 root   tty       4,  10 2011-05-29 00:30 tty10
crw--w----   1 root   tty       4,  11 2011-05-29 00:30 tty11
crw--w----   1 root   tty       4,  12 2011-05-29 00:30 tty12
crw--w----   1 root   tty       4,  13 2011-05-29 00:30 tty13
crw--w----   1 root   tty       4,  14 2011-05-29 00:30 tty14
crw--w----   1 root   tty       4,  15 2011-05-29 00:30 tty15
crw--w----   1 root   tty       4,  16 2011-05-29 00:30 tty16
crw--w----   1 root   tty       4,  17 2011-05-29 00:30 tty17
crw--w----   1 root   tty       4,  18 2011-05-29 00:30 tty18
crw--w----   1 root   tty       4,  19 2011-05-29 00:30 tty19
crw-------   1 ubuntu tty       4,   2 2011-05-29 00:30 tty2
crw--w----   1 root   tty       4,  20 2011-05-29 00:30 tty20
crw--w----   1 root   tty       4,  21 2011-05-29 00:30 tty21
crw--w----   1 root   tty       4,  22 2011-05-29 00:30 tty22
crw--w----   1 root   tty       4,  23 2011-05-29 00:30 tty23
crw--w----   1 root   tty       4,  24 2011-05-29 00:30 tty24
crw--w----   1 root   tty       4,  25 2011-05-29 00:30 tty25
crw--w----   1 root   tty       4,  26 2011-05-29 00:30 tty26
crw--w----   1 root   tty       4,  27 2011-05-29 00:30 tty27
crw--w----   1 root   tty       4,  28 2011-05-29 00:30 tty28
crw--w----   1 root   tty       4,  29 2011-05-29 00:30 tty29
crw-------   1 ubuntu tty       4,   3 2011-05-29 00:30 tty3
crw--w----   1 root   tty       4,  30 2011-05-29 00:30 tty30
crw--w----   1 root   tty       4,  31 2011-05-29 00:30 tty31
crw--w----   1 root   tty       4,  32 2011-05-29 00:30 tty32
crw--w----   1 root   tty       4,  33 2011-05-29 00:30 tty33
crw--w----   1 root   tty       4,  34 2011-05-29 00:30 tty34
crw--w----   1 root   tty       4,  35 2011-05-29 00:30 tty35
crw--w----   1 root   tty       4,  36 2011-05-29 00:30 tty36
crw--w----   1 root   tty       4,  37 2011-05-29 00:30 tty37
crw--w----   1 root   tty       4,  38 2011-05-29 00:30 tty38
crw--w----   1 root   tty       4,  39 2011-05-29 00:30 tty39
crw-------   1 ubuntu tty       4,   4 2011-05-29 00:30 tty4
crw--w----   1 root   tty       4,  40 2011-05-29 00:30 tty40
crw--w----   1 root   tty       4,  41 2011-05-29 00:30 tty41
crw--w----   1 root   tty       4,  42 2011-05-29 00:30 tty42
crw--w----   1 root   tty       4,  43 2011-05-29 00:30 tty43
crw--w----   1 root   tty       4,  44 2011-05-29 00:30 tty44
crw--w----   1 root   tty       4,  45 2011-05-29 00:30 tty45
crw--w----   1 root   tty       4,  46 2011-05-29 00:30 tty46
crw--w----   1 root   tty       4,  47 2011-05-29 00:30 tty47
crw--w----   1 root   tty       4,  48 2011-05-29 00:30 tty48
crw--w----   1 root   tty       4,  49 2011-05-29 00:30 tty49
crw--w----   1 root   tty       4,   5 2011-05-29 00:30 tty5
crw--w----   1 root   tty       4,  50 2011-05-29 00:30 tty50
crw--w----   1 root   tty       4,  51 2011-05-29 00:30 tty51
crw--w----   1 root   tty       4,  52 2011-05-29 00:30 tty52
crw--w----   1 root   tty       4,  53 2011-05-29 00:30 tty53
crw--w----   1 root   tty       4,  54 2011-05-29 00:30 tty54
crw--w----   1 root   tty       4,  55 2011-05-29 00:30 tty55
crw--w----   1 root   tty       4,  56 2011-05-29 00:30 tty56
crw--w----   1 root   tty       4,  57 2011-05-29 00:30 tty57
crw--w----   1 root   tty       4,  58 2011-05-29 00:30 tty58
crw--w----   1 root   tty       4,  59 2011-05-29 00:30 tty59
crw-------   1 ubuntu tty       4,   6 2011-05-29 00:30 tty6
crw--w----   1 root   tty       4,  60 2011-05-29 00:30 tty60
crw--w----   1 root   tty       4,  61 2011-05-29 00:30 tty61
crw--w----   1 root   tty       4,  62 2011-05-29 00:30 tty62
crw--w----   1 root   tty       4,  63 2011-05-29 00:30 tty63
crw--w----   1 root   tty       4,   7 2011-05-29 00:30 tty7
crw--w----   1 root   tty       4,   8 2011-05-29 00:30 tty8
crw--w----   1 root   tty       4,   9 2011-05-29 00:30 tty9
crw-------   1 root   root      5,   3 2011-05-29 00:30 ttyprintk
crw-rw----   1 root   dialout   4,  64 2011-05-29 00:30 ttyS0
crw-rw----   1 root   dialout   4,  65 2011-05-29 00:30 ttyS1
crw-rw----   1 root   dialout   4,  74 2011-05-29 00:30 ttyS10
crw-rw----   1 root   dialout   4,  75 2011-05-29 00:30 ttyS11
crw-rw----   1 root   dialout   4,  76 2011-05-29 00:30 ttyS12
crw-rw----   1 root   dialout   4,  77 2011-05-29 00:30 ttyS13
crw-rw----   1 root   dialout   4,  78 2011-05-29 00:30 ttyS14
crw-rw----   1 root   dialout   4,  79 2011-05-29 00:30 ttyS15
crw-rw----   1 root   dialout   4,  80 2011-05-29 00:30 ttyS16
crw-rw----   1 root   dialout   4,  81 2011-05-29 00:30 ttyS17
crw-rw----   1 root   dialout   4,  82 2011-05-29 00:30 ttyS18
crw-rw----   1 root   dialout   4,  83 2011-05-29 00:30 ttyS19
crw-rw----   1 root   dialout   4,  66 2011-05-29 00:30 ttyS2
crw-rw----   1 root   dialout   4,  84 2011-05-29 00:30 ttyS20
crw-rw----   1 root   dialout   4,  85 2011-05-29 00:30 ttyS21
crw-rw----   1 root   dialout   4,  86 2011-05-29 00:30 ttyS22
crw-rw----   1 root   dialout   4,  87 2011-05-29 00:30 ttyS23
crw-rw----   1 root   dialout   4,  88 2011-05-29 00:30 ttyS24
crw-rw----   1 root   dialout   4,  89 2011-05-29 00:30 ttyS25
crw-rw----   1 root   dialout   4,  90 2011-05-29 00:30 ttyS26
crw-rw----   1 root   dialout   4,  91 2011-05-29 00:30 ttyS27
crw-rw----   1 root   dialout   4,  92 2011-05-29 00:30 ttyS28
crw-rw----   1 root   dialout   4,  93 2011-05-29 00:30 ttyS29
crw-rw----   1 root   dialout   4,  67 2011-05-29 00:30 ttyS3
crw-rw----   1 root   dialout   4,  94 2011-05-29 00:30 ttyS30
crw-rw----   1 root   dialout   4,  95 2011-05-29 00:30 ttyS31
crw-rw----   1 root   dialout   4,  68 2011-05-29 00:30 ttyS4
crw-rw----   1 root   dialout   4,  69 2011-05-29 00:30 ttyS5
crw-rw----   1 root   dialout   4,  70 2011-05-29 00:30 ttyS6
crw-rw----   1 root   dialout   4,  71 2011-05-29 00:30 ttyS7
crw-rw----   1 root   dialout   4,  72 2011-05-29 00:30 ttyS8
crw-rw----   1 root   dialout   4,  73 2011-05-29 00:30 ttyS9
drwxr-xr-x   8 root   root         180 2011-05-29 04:41 .udev
crw-r-----   1 root   root     10, 223 2011-05-29 00:30 uinput
crw-rw-rw-   1 root   root      1,   9 2011-05-29 00:30 urandom
crw-------   1 root   root    252,   0 2011-05-29 00:30 usbmon0
crw-------   1 root   root    252,   1 2011-05-29 00:30 usbmon1
crw-------   1 root   root    252,   2 2011-05-29 00:30 usbmon2
crw-------   1 root   root    252,   3 2011-05-29 00:30 usbmon3
crw-------   1 root   root    252,   4 2011-05-29 00:30 usbmon4
crw-------   1 root   root    252,   5 2011-05-29 00:30 usbmon5
drwxr-xr-x   4 root   root          80 2011-05-29 00:30 v4l
crw-rw----   1 root   tty       7,   0 2011-05-29 00:30 vcs
crw-rw----   1 root   tty       7,   1 2011-05-29 00:30 vcs1
crw-rw----   1 root   tty       7,   2 2011-05-29 00:30 vcs2
crw-rw----   1 root   tty       7,   3 2011-05-29 00:30 vcs3
crw-rw----   1 root   tty       7,   4 2011-05-29 00:30 vcs4
crw-rw----   1 root   tty       7,   5 2011-05-29 00:30 vcs5
crw-rw----   1 root   tty       7,   6 2011-05-29 00:30 vcs6
crw-rw----   1 root   tty       7,   7 2011-05-29 00:30 vcs7
crw-rw----   1 root   tty       7, 128 2011-05-29 00:30 vcsa
crw-rw----   1 root   tty       7, 129 2011-05-29 00:30 vcsa1
crw-rw----   1 root   tty       7, 130 2011-05-29 00:30 vcsa2
crw-rw----   1 root   tty       7, 131 2011-05-29 00:30 vcsa3
crw-rw----   1 root   tty       7, 132 2011-05-29 00:30 vcsa4
crw-rw----   1 root   tty       7, 133 2011-05-29 00:30 vcsa5
crw-rw----   1 root   tty       7, 134 2011-05-29 00:30 vcsa6
crw-rw----   1 root   tty       7, 135 2011-05-29 00:30 vcsa7
crw-------   1 root   root     10,  63 2011-05-29 00:30 vga_arbiter
crw-rw----+  1 root   video    81,   0 2011-05-29 00:30 video0
crw-rw-rw-   1 root   root      1,   5 2011-05-29 00:30 zero
ubuntu@ubuntu:~$ fuser -m /dev/sdd2
Cannot stat file /proc/4000/fd/21: Stale NFS file handle
Cannot stat file /proc/4000/fd/22: Stale NFS file handle
Cannot stat file /proc/4000/fd/41: Stale NFS file handle
Cannot stat file /proc/4000/fd/42: Stale NFS file handle
ubuntu@ubuntu:~$ ps --pid 4000
  PID TTY          TIME CMD
 4000 ?        00:00:06 nautilus
ubuntu@ubuntu:~$

---

### Post by eddiekoski on 2011-05-29
I really wish there was a way to force ubuntu to take control of drive and mount

---

### Post by eddiekoski on 2011-05-29
It does recommend using another  linux distribution that could be willing to take the risk of force mounting the drive. I may try that or I may try the open solaris disk.

---

