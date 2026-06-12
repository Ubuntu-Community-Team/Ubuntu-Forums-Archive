---
title: "fstab From Kubuntu Does Not Work With Ubuntu.  Need Assistance."
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by umechanism on 2008-08-26
[SIZE="1"]

I used Kubuntu for about 8 months then, on a whim, decided to try Ubuntu.  I saved all my critical /etc/.... data and especially my /etc/fstab.  I basically uninstalled Kubuntu and installed Ubuntu then replaced all the files, including my fstab file with the ones from Kubuntu.  

Well, for some reason, I can not mount the same HP Media Vault (network storage device) in Ubuntu that I had mounted in Kubuntu using the same fstab file.  Am I missing something here????

I can mount the Media Vault by choosing "Place>Network>Windows Network>Window Shares>" then the folders I want BUT it does not get mounted in the /mnt directory which is where I want it.

Below is my fstab file.  If you can help or see anything wrong with what I am doing please let me know.

The Media Vault's address is the 192.168.2.102 shown in the fstab below.

Thank You. 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d8efe242-3278-4cd7-a8b7-2e9fcb0e90ae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=936348d1-fff4-471f-9de0-07d63a27baf8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.2.102:/shares/Volume1/FileShare /mnt/mediavault/FileShare nfs defaults 0 0
//192.168.2.102:/shares/Volume1/Backup /mnt/mediavault/BackUp nfs defaults 0 0
//192.168.2.102:/shares/Volume1/CinemaNow /mnt/mediavault/CinemaNow nfs defaults 0 0
//192.168.2.102:/shares/Volume1/MediaShare /mnt/mediavault/MediaShare nfs defaults 0 0

/dev/sda1 /mnt/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
<device> /media auto users,atime,noauto,rw,nodev,exec,nosuid 0 0
dev/sdb1 /media/20gig nfs nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1[/SIZE]

---

### Post by jigsaws on 2008-08-26
What shows:
sudo mount
and
sudo mount -a
?

---

### Post by umechanism on 2008-08-26
> **jigsaws said:**
> What shows:
sudo mount
and
sudo mount -a
?

Thanks for the reply.  See below.

michael@Michael-Ubuntu:/**$ sudo mount**
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=michael)
michael@Michael-Ubuntu:/$ 
michael@Michael-Ubuntu:/$ 


michael@Michael-Ubuntu:/$ **sudo mount -a**
mount: wrong fs type, bad option, bad superblock on //192.168.2.102:/shares/Volume1/Backup,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fuse: failed to access mountpoint /mnt/Windows: No such file or directory
mount: mount point /media/20gig does not exist
michael@Michael-Ubuntu:/$

---

### Post by PaulClarke on 2008-08-26
Hello Michael,

I'm sorry but I cannot help you but I do have almost exactly the same problem.  In my case the fstab works in Fedora but not in Ubuntu.

Paul

---

### Post by umechanism on 2008-08-26
Well, I've not used Fedora but Ubuntu and Kubuntu are the same "Linux" with different GUI's so their fstab files should be interchangeable.  It is a mystery to me why mine is not.

Mike

---

### Post by jigsaws on 2008-08-27
First of all // before IP look wired and it can be just:
192.168.2.102:/shares/Volume1/FileShare

but this is not the problem I think. Have you got nfs-common installed? Try:

sudo apt-get install nfs-common

---

### Post by umechanism on 2008-08-27
> **jigsaws said:**
> First of all // before IP look wired and it can be just:
192.168.2.102:/shares/Volume1/FileShare

but this is not the problem I think. Have you got nfs-common installed? Try:

sudo apt-get install nfs-common

That was it!  I did not have NFS Common installed.  I installed it, executed "mount -a" and all remote folders are mounted correctly.

Thank you!!!

---

