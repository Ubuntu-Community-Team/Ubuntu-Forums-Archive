---
title: "Problem sharing a drive using Samba - Easy for an expert!"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Ted_Smith on 2007-09-14
I have a folder that I am trying to share on a reiser partition using Samba. I have 'enabled sharing' of the folder (right clicked, share folder, selected Samba etc). I have enabled my samba user account (sudo smbpasswd -e ted) and set the samba password for my user account using smbpasswd ( sudo smbpasswd -a ted). However, every time I try to connect from another Ubuntu machine on my network using the mount command (sudo mount 123.456.789.123:/home/ted/MountPoint/SharedDrive LocalMountPoint/SharedDrive) it says "Mount: failed. Reason given by server : Permission is denied".

So I tried it with NFS instead. Ensured there was an entry in /etc/exports, and ensured I executed both 'sudo /etc/init.d/nfs-common restart' and 'sudo /etc/init.d/nfs-kernel-server restart'. But when I try to mount (sudo mount -t nfs 123.456.789.123:/home/ted/MountPoint/SharedDrive LocalMountPoint/SharedDrive), same error. 

Can anyone help? I've asked several times on IRC and no one can assist. 

Cheers

Ted

---

### Post by rivalarrival on 2007-09-14
Check your smb.conf file (/etc/samba/smb.conf) for the proper share name - I don't think it should be "/home/ted/MountPoint/SharedDrive".

gedit /etc/samba/smb.conf
find "/home/ted/MountPoint/SharedDrive"
and look for what is in square brackets above that section.

```

[ShareName]
public = yes
path = /home/ted/MountPoint/SharedDrive
writeable = yes
browesable = yes
create mask = 0660
directory mask = 0770

```

Samba will share this folder as "ShareName" not as "/home/ted/MountPoint/SharedDrive" - change your mount command to 
```
sudo mount 123.456.789.123:ShareName /LocalMountPoint/SharedDrive
```

---

### Post by Ted_Smith on 2007-09-16
Thanks a lot for your help. But I'm afraid that doesn't work either. I reverted back to Samba, checked the log file as you said, and sure enough there is a section called [SCSI] as you describe. So I tried 

sudo mount 192.162.1.5:/SCSI Mounts/SCSIShare

and

sudo mount 192.162.1.5:SCSI Mounts/SCSIShare

and 

sudo mount -t reiser 192.162.1.5:/SCSI Mounts/SCSIShare

and none worked. They all returned the same error as above :-(

---

