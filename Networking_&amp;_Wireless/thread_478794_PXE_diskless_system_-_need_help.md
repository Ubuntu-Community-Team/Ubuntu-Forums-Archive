---
title: "PXE diskless system - need help"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by dannyboy1121 on 2007-06-19
Hi folks,

Worked my way through several tutorials on this subject - trying my best to get a diskless Linux system up and running based on Edgy. (mainly working from [https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto"))

I'm confident that my DHCP and TFTP (hosted on a hacked NSLU2 which is also my NFS server) settings are working correctly because I've been able to get the ubuntu netboot installations to kick off an install (alas I have no drive to install to - this system has to be diskless).

When I'm trying to configure a diskless booting system - it appears to run the kernal and then the initrd loads - everything appears to start and then I get -

 ***Kernal Panic - not syncing: Attempted to kill init!***

... hang ...

I need some help troubleshooting the cause of the error.

The kernal was copied off my laptop and the initrd was created with mkinitramfs - with the initramfs.conf amended to use NFS for boot.

Here's my default file contents:

LABEL linux
KERNEL vmlinuz-2.6.17-11-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.17-11-generic nfsroot=192.168.1.50:/nfsroot ip=dhcp rw

Here's my NFS export entry:

/nfsroot        192.168.1.0/255.255.255.0(rw,no_root_squash,async)

I've copied all the relevant directories across to my nfsroot - and scrubbed references to eth0 and set up fstab as follows:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     defaults        0       0
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults        0       0


Any advice would be appreciated. I've picked google dry on this topic and I'm obviously missing something fundamental.

Regards

---

### Post by bbmak on 2007-06-19
Are you doing this in windows server?
because if you are trying to using windows pxe to boot linux os system, i am able to help you. If you are doing pure Linux, sorry.

---

### Post by dannyboy1121 on 2007-06-20
Pure linux - no windows.

Anyone else?

---

### Post by dannyboy1121 on 2007-06-20
No - really, this is the last time I bump this thread. I guess not many people PXE boot.

---

### Post by dannyboy1121 on 2007-06-20
Just in case some other hapless soul is attempting a diskless PXE booted system - and encounters the same issue - it turns out that mine was with the kernel that I used.

Now I've compiled my own from Kernal.org - ensured appropriate NFS support etc and the system finally began to boot. I just have to iron out some of the kinks with the FS I've copied across to my NFS root to get the thing running straight.

---

