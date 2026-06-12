---
title: "Extracting Windows Files"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Martin Houlton on 2011-09-03
Hi, I have a dual-boot Windows Vista/Ubuntu 11.04 system, with Ubuntu installed on the hard disc, not a CD. Everything is working fine, but my question is: how do I get files out of the Windows partition into the Ubuntu partition? I looked at mount in the terminal, but it seems to only handle volumes that are already mounted. The output of mount is:

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/martin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=martin)

Help appreciated.

---

### Post by oldfred on 2011-09-03
You have installed wubi which is inside the NTFS windows partition. Look in hosts in the left panel of Nautilus and you should find windows. You have in you list form mount /host.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by Martin Houlton on 2011-09-03
Thanks oldfred, I can see my Windows folders and files now, only problem is all my files are greyed out and I cannot access them.

---

### Post by bcbc on 2011-09-03
You should have full access to the /host - how are you accessing it? 

But you don't want to copy files from the /host to your wubi virtual disk:
On the /host, each file is a physical file stored on a disk partition. On the Wubi virtual disk each file is stored on a virtual partition within a single physical file. So it's safer to leave files on the /host.

It's also harder to get at the files while in Windows if you copy them onto the virtual disk.

---

### Post by Martin Houlton on 2011-09-04
bcbc, I think I was accessing it via the the Search For Files gadget, but I just tried opening a file from /host into LibreOffice, and it worked fine.

---

