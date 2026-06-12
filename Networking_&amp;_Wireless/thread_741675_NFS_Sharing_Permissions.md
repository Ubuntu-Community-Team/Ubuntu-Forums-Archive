---
title: "NFS Sharing Permissions"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by zorneatsham on 2008-04-01
I have a folder on my Ubuntu server which I have set up to share with my Mac via NFS. It is also set up to share via SSH for remote access by my fiancee (she's in another state). I have the folder set to be read only for Others, but I want to be able to edit the files from my Mac and have other users only be able to read. This folder contains my iTunes library for my Mac, so I need to be able to edit. The only way that I can currently have write access is if I allow the folder to be editable by everyone.

Thanks,

Zach

---

### Post by Eiríkr on 2008-04-01
This sounds very much like a filesystems permission configuration issue.  From what I understand, it sounds like you have two users -- yourself, and your fiancee.  I'd recommend that you create a group, perhaps called **sshshare**.  Then add your fiancee to this group.
```
sudo addgroup sshshare
sudo usermod -aG sshshare fiancee
```

Make this group the primary group for the shared folder and all contents, with your own username **zorneatsham** (or whatever it really is) as the owner:
```
sudo chown -R zorneatsham:sshshare /path/to/share
```

Then change the permissions on the shared directory so that the owner can write, but group members can only read, and others can't do anything (for security's sake).  In addition, to ensure that any sub-directories created within the share inherit the shared directory's primary group, add the [font=courier]setgid[/font] bit (the leading "2" in chmod octal) just to directory permissions (the "-type d" option to the find command):
```
sudo chmod -R 0750 /path/to/share
find /path/to/share -type d -print0 | sudo xargs -0 chmod 2750
```

Note that this assumes that your UID is the same on your Mac and your Ubuntu server.  

HTH,

Eiríkr

---

