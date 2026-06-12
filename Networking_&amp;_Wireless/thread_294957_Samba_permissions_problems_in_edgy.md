---
title: "Samba permissions problems in edgy"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by nickspoon on 2006-11-07
I have started using SMB to share files between Edgy and other PCs. However, whilst the share shows up, it is inaccessible. If I try to smbmount it from another Linux device, I get an ERRNOSUCHSHARE. smbd says the error is "Permission Denied", but it is running as root and 'chmod -R 777 shared_dir' does not have any effect on accessibility.

Using edgy, visiting smb://localhost in Nautilus shows the shared folder, but double-clicking on it produces an error box:

The folder contents could not be displayed.
"shared_dir" couldn't be found. Perhaps it has recently been deleted.

(The folder is still there, and is shared)

The folder entry in smb.conf is:

[shared_dir]
path = /home/nick/shared_dir
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by dmizer on 2006-11-08
try configuring samba via stormbringer's guide here: [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

if that doesn't sound apealing to you, try changing "shared_dir" in the brackets to "homes" so it looks like this:
```
[homes]
path = /home/nick/shared_dir
available = yes
browsable = yes
public = yes
writable = yes
```
restart samba, and see if you can view it in nautilus.  but recently, i've been seeing a lot of people having problems with nautilus and samba, so there could be other issues at work here.

---

