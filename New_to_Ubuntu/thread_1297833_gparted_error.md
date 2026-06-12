---
title: "gparted error"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by expatCM on 2009-10-22
I am trying to format an external hard drive to ext4.  I got an error message which is below and the drive does not appear in gparted now.

The reason I decided to format was that the then ext3 file system was not recognized and could not be recovered with fsck.  No idea why I got the first problem ... happens I guess but I am wondering if the second challenge is a suggestion of some deeper issue.

So I am wondering if there are any suggestions of what next?


```
GParted 0.4.3

Libparted 1.8.8
Format /dev/sdd1 as ext4  00:03:20    ( ERROR )
     	
calibrate /dev/sdd1  00:00:00    ( SUCCESS )
     	
path: /dev/sdd1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
set partition type on /dev/sdd1  00:00:19    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:02:55    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000

Writing inode tables: done
mke2fs 1.41.4 (27-Jan-2009)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

========================================

```

---

### Post by bumanie on 2009-10-22
Are you using usb 1.1 or usb 2.0? I had trouble with gparted when the external hard drive was accidenatally plugged into a usb 1.1 port - once I realized and changed it to the usb 2.0 port, formatting worked fine. Worth checking the speed of the usb port that the external drive is plugged in to.

---

### Post by HarrisonNapper on 2009-10-22
Are you running GParted Live or from within Ubuntu. Make sure you're running as su and that the filesystem you're trying to format is unmounted.

How long have you been having issues with this HDD (including the fsck issues)? Could be a problem with the hard-drive itself, too (depending on how old it is, how it's installed in your PC, etc)

Cheers.

---

### Post by expatCM on 2009-10-22
The USB port is 2.0 and the same port as used successfully in the past.

I am running gparted from within Ubuntu on the desktop install.

The drive is a WD 1GB.  I cannot help but wonder if it is the drive ....  I know that drives are very reliable now but I just managed to get the drive recognized again.  This time I was able to watch gparted try to format the partition ...  basically the process hanged or at least did not complete after 90 minutes.

I deleted the partition and created a new one.  That works.  When the partition is formatted to ext4 nothing seems to happen.  There does not appear to be rw activity from the drive and the process says it is running but does not seem to do so or at least there is no result ....

---

### Post by HarrisonNapper on 2009-10-22
This is a 1GB external? Old skool. A few questions: Is the connector on the external HD USB 1.* or 2.*? Can you post the terminal output from the most recent run?

That's all for now. :)

---

### Post by expatCM on 2009-10-23
oops sorry, my mistake ....  it is 500GB.

How can I find out what the speed of the USB port is on the external housing?

But also ....  I was wondering why this is going to be important since the drive used to work in this housing and on the same port on the motherboard but does not work now in that the drive cannot format ....

---

