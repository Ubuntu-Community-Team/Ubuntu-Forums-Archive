---
title: "Cannot get nfs to work"
date: 2016-08-14
forum: Networking &amp; Wireless
---

### Post by philsweeney on 2016-08-14
I have followed the NFS install and another post. I have attached from the server: exports, and fstab. The folder is amanda_photos. The server is "gateway" (192.168.3.1).
One client is phil-network (192.168.3.2) I have not used any login passwords and at boot the client states problem mounting /mnt/amanda_photos.
I believe the following is all the pertinent terminal info from each machine. I have been using putty to get in the server.

login as: phil
phil@192.168.3.1's password:
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-34-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

2 packages can be updated.
0 updates are security updates.


Last login: Sun Aug 14 08:35:51 2016 from 192.168.3.2
phil@gateway:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subt                                                                                                                                                                                                                                             ree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
/mnt/amanda_photos 192.168.3.0/255.255.255.128 (rw,sync,no_subtree_check)

phil@gateway:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=15b935f1-10e6-4bd1-b5cd-298d57693296 /               ext4    errors=remount                                                                                                                                                                                                                                             -ro 0       1
# swap was on /dev/sda5 during installation
UUID=2b5aec90-963f-4c99-b79a-278d01a05680 none            swap    sw                                                                                                                                                                                                                                                           0       0
#
# /dev/sdb1: LABEL="amanda_photos" UUID="02FEB4015142166F" TYPE="ntfs" PARTUUID=                                                                                                                                                                                                                                             "0264f305-01"
UUID=02FEB4015142166F                     /mnt            ntfs    errors=remount                                                                                                                                                                                                                                             -ro 0       1
#
phil@gateway:~$

phil@phil-network:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=7731c534-f5ca-4734-8a4d-bfbf63730ac3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45ada9f4-145d-4b9b-b1cf-0b514a3467de /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=b879c578-0982-4246-91d7-570eec5c084a none            swap    sw              0       0
#
192.168.3.1: /mnt/amanda_photos /media/phil/photos nfs rw,hard,intr 0 0
#

phil@phil-network:~$ cd ..
phil@phil-network:/home$ cd ..
phil@phil-network:/$ dir
amanda_photos  dev       initrd.img.old  local       opt   sbin  usr
bin           etc       lib           lost+found  proc  srv   var
boot           home       lib32       media       root  sys   vmlinuz
cdrom           initrd.img  lib64       mnt           run   tmp   vmlinuz.old
phil@phil-network:/$ cd media
phil@phil-network:/media$ ls
phil
phil@phil-network:/media$ ls
phil
phil@phil-network:/media$ cd phil
phil@phil-network:/media/phil$ ls
photos
phil@phil-network:/media/phil$ ^C
phil@phil-network:/media/phil$

---

