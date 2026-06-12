---
title: "smbfs write permissions"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by farscape on 2007-03-31
I have ubuntu set up to automount a few windows shares at boot up.

I edit  fstab
**sudo gedit /etc/fstab**

I add **//WindowsMachine/WindowsShare /mnt_directory smbfs username=WinUserName,password=WinPassword  0   0**

It works great. Mounts at boot up. Very nice. I can stream music/video from these shares. 
Problem is that I don't have write permissions on these shares. ReadOnly.
In WIndows, I do have the shares set to "allow network users to change my files"

Is there something in the fstab command I'm missing?
//WindowsMachine/WindowsShare /mnt_directory smbfs username=WinUserName,password=WinPassword  0   0

---

### Post by prensing on 2007-03-31
Yes, you need to set some more options. The useful ones for this are:
   uid  - sets the owner of the files on your box
   gid  - sets the group of the files on your box
   fmask  - sets the permission bits on files
   dmask  - similar for directories

So, you can set the files to be owned by you, especially if this is a single user machine. If you want multiple users to be able to write, then you might need to create a specific group for it and set it so the files/directories are group-writable.

---

### Post by farscape on 2007-03-31
> **prensing said:**
> Yes, you need to set some more options. The useful ones for this are:
   uid  - sets the owner of the files on your box
   gid  - sets the group of the files on your box
   fmask  - sets the permission bits on files
   dmask  - similar for directories

So, you can set the files to be owned by you, especially if this is a single user machine. If you want multiple users to be able to write, then you might need to create a specific group for it and set it so the files/directories are group-writable.

Thanks, I just added uid=1000 to the string. It looks like this now. 

//WindowsMachine/WindowsShare /mnt_directory smbfs uid=1000,username=WinUserName,password=WinPassword 0 0

I can read and write now. Thanks.

---

