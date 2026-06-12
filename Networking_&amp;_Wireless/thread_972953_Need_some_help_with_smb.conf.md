---
title: "Need some help with smb.conf"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by xadloki on 2008-11-06
I've been trying to setup samba for the last 3 days to work the way I want it but I'm stuck with this problem that I just can't seem to solve.
If I authenticate with user1 the drive mounts and I have the access to the shares just fine. For this to work I had to remove the libpam-smbpass package because it was messing up the access passwords everytime I restarted samba.

But my main problem now is getting user2 to have access to the shares. I have the permissions set correctly so that user1 and user2 are in the same group that has rw permissions to the shares user1 being the owner. When I log on with user2 it accepts the password but once the dialog to select which share to mount (in mac os x leopard) it gives me the message that could not mount.

User1 and user2 were both added with smbpasswd and are enabled, I can see them listed in "pdbedit -Lw". 

My smb.conf is below, anyone have any suggestions to what might be missing here? Thanks.

```
[global]

workgroup = WORKGROUP
hosts allow = 127.0.0.1, 192.168.X.XXX, 192.168.X.XXX
hosts deny = 0.0.0.0/0

security = user
encrypt passwords = true
passdb backend = tdbsam
username map = /etc/samba/smbusers
map to guest = bad user
guest account = nobody
create mask = 0644
directory mask = 0755

#### Logging ####

log file = /var/log/samba/log.%m
max log size = 1000
syslog only = no
syslog = 0

#### Shares ####

[share1]
comment = Share1
path = /mnt/301/share1
guest ok = yes
browseable = yes
read only = yes
valid users = user1 user2
write list = user1

[share2]
comment = Share2
path = /mnt/301/share2
browseable = yes
read only = yes
valid users = user1 user2
write list = user1
```

---

### Post by superprash2003 on 2008-11-06
but only user1 seems to be on the write list and not user2

---

### Post by xadloki on 2008-11-06
Well I don't want to give user2 write permission, only read. That should not effect the mounting of the volume.

---

### Post by xadloki on 2008-11-08
Well I solved it finally so I'll post this in case anyone runs in to a similar problem.

User1 could access the shares because he has owner permissions in /media/hd1/ and most of the subdirectories on that disk. Also the group was set to user1 instead of "users". This means that User2 even though he had permissions to access certain subfolders in hd1 samba would not allow mounting because user2 had no access to the parent directory.

---

