---
title: "How to mount remote files"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-04-24
Hi,

I have two computers: glen-laptop and glen-desktop.  I have an external hard drive pluged into glen-desktop formatted as ntfs.  I want to mount the hard drive on the laptop.

I have installed samba on the desktop and have shared the hard drive.  I can access it by going to smb://glen-desktop/GLEN'S HDD

But I need it mounted into the local file system.  How do I do this?  I have tried creating a directory /mnt/GLEN'S HDD and editing /etc/fstab to include 
```
//glen-desktop/"GLEN'S HDD" /mnt/"GLEN'S HDD" smb default 0 0
```
and then typing 
```
sudo mount /mnt/"GLEN'S HDD"
``` 

But it gives this error:
```
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /mnt/GLEN'S HDD in /etc/fstab or /etc/mtab

```

---

### Post by Peter09 on 2009-04-24
Although I am not sure of the problem, I would be wary about using the ' in the path. Linux can take some of these characters to mean other things.

---

### Post by JoshuaRL on 2009-04-24
I'd suggest smb4k.  I use that myself, and it really makes things easy.  It mounts samba shares in a "smb4k" folder in your /home.  If you're using Gnome, you can use the Places menu and connect to server.  Just save the settings to a bookmark and it will be easy to reconnect.  Right now I've got my samba shares mounted, and my server root files (mounted with sftp with the "SSH" option under the same Places menu).  Really slick.

---

