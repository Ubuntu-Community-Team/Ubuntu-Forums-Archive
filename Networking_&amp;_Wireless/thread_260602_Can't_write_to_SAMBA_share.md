---
title: "Can't write to SAMBA share"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by hipnerd on 2006-09-19
I recently began dual-booting with Ubuntu and WinXP and I believe I am ready to take the plunge and make Ubuntu my primary OS.

I had already built a Debian-based file server for my network, and all my Windows boxes can access it easily with both read and write privleges. I am not having as much luck getting Ubuntu to work. I can read any of the folders shared on the network server, but I seem to have no write privledges. 

I assume this is basic, rookie stuff, but all my Windows knowledge is not helping here at all. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
//SERVER1/mp3    /media/mp3s smbfs  credentials=/root/.smbcredentials    0    0
//SERVER1/comics    /media/comics smbfs  credentials=/root/.smbcredentials    0    0
//SERVER1/photos    /media/photos smbfs  credentials=/root/.smbcredentials    0    0

```

Anyone want ot help the newbie out?

---

### Post by mwcinc on 2006-09-19
Try changing the last three lines to:

//SERVER1/mp3    /media/mp3s smbfs  credentials=/root/.smbcredentials,uid=your_login_name,gid=your_group,dmask=777,fmask=777    0    0
//SERVER1/comics    /media/comics smbfs  credentials=/root/.smbcredentials,uid=your_login_name,gid=your_group,dmask=777,fmask=777    0    0
//SERVER1/photos    /media/photos smbfs  credentials=/root/.smbcredentials,uid=your_login_name,gid=your_group,dmask=777,fmask=777    0    0


You will need to replace "your_login_name" and "your_group" of course.

Regards,
M.W.

---

### Post by hipnerd on 2006-09-19
Okay, I tried that. I replaced uid with my username and gid with the workgroup I created then remounted fstab with "sudo mount -a"

I have the same problem. All files say they are owned by root. I can't change them or write new files to those folders.

---

### Post by gnu2tux on 2006-09-19
Who owns /media and all the directories underneath, you or root?

if it's root:

sudo chown -R <yourusername> /media

(youll need to unmount your shares first though)

Regards,

Al

---

### Post by hipnerd on 2006-09-19
That did it. Thank you very much. I solved this and my problem configuring compiz in just a few posts. The community has been very helpful.

---

### Post by gnu2tux on 2006-09-19
glad we could be of assistance

---

