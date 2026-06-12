---
title: "Sharing an Optical Drive between Ubuntu boxes"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Glenhawk on 2007-12-02
Hello all,
I have a tricky problem that I am close to solving but am currently beating my head against a wall. ](*,)

I have shared my cdrom (DVD Optical Disk Drive - ODD) using samba... (smb.conf)
[INDENT][cdrom]
comment = glen-desktop ODD
writable = no
locking = no
path = /cdrom
public = yes[/INDENT]

...and with windows it works great. I can put in a DVD with media files on it and the windows PC will be able to play them but it won't lock up the drive. In other words after I am finished with the Disc I can eject it.
When I try to open the Disc from my Mythbuntu Frontend (Xubuntu) using fstab becasue it is the only way I know how, I can no longer eject the disc becasue it is "Locked by an application".
I must need either a particular setting in fstab or a way of mounting the shared ODD that doesn't use fstab. 
Any suggestions?

fstab lines tried:
[INDENT]//glen-desktop/cdrom   /media/serverODD/    smbfs    0    0  #this works but locks the drive

//glen-desktop/cdrom   /media/serverODD/    smbfs    noauto    0    0  #this does not mount

//glen-desktop/cdrom   /media/serverODD/    smbfs   user,noauto,exec     0    0  #these are options copied from a locally mounted ODD but the disc still won't mount[/INDENT]

:guitar:

(edit)
Got it sorted - I am using fuse on the Mythbuntu (xubuntu) box. I have set fuse to mount the network in a particular directory and I can now browse the directory just like you would from a windows box. 

The only real impact is that to specify directory I now have to use something like:
/media/network/MSHOME/Ubuntu-Server/Multimedia/TVShows
instead of the fstab version...
/media/Multimedia/TVShows

...but at least I can now access an optical drive from my miniature PC under my TV and it doesn't lock me out of it from the server.

---

