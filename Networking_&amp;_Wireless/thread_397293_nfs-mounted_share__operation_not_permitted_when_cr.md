---
title: "nfs-mounted share / operation not permitted when creating a new file"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by NoHoSe on 2007-03-30
hello,

I'm having some weird problem with NFS. Installation is OK, mounting no problem, I can read and modify files on a NFS mounted directory. The problem comes when I try to create a new file, then I receive an "Operation not permitted", the file is created anyway, but with length 0 bytes. If later I modify that file, everything is OK. This happens both at command line and from applications.

On the NFS server no problem at all.

Some additional information:
- on the NFS server, the directory I want to share is a FAT32 disk
- I have this problem with all users with gid=2000 on client machines, and none of them belongs to more than 16 groups. On the server, as mentioned, no problem at all

Here are the relevant lines in my config files:

* /etc/fstab on server: 
/dev/hda5 /media/hda5 vfat rw,dev,auto,noexec,utf8,gid=2000,posix,fmask=117,dmask=007 0 1

* /etc/exports on server:
/media/hda5     192.168.1.0/255.255.255.0(rw)

* /etc/fstab on clients:
kitaro.localdomain:/media/hda5 /media/CRCC nfs rsize=8192,wsize=8192,rw,soft,noac,intr 0 0

Am I missing anything? I'm getting nuts here, any help most appreciated.

Thanks

---

### Post by notepad on 2008-01-27
i am having the exact same problem as you describe. im looking into it and if i find anything i will post here again.

edit: im looking into the fstab for the answer. i think i need to set uninhibited write access to the directory being shared which since it is fat32, is a nightmare.
update: tried changing umask to 000 in fstab and rebooting. while that changed permissions locally, it didnt help my nfs error at all.

---

