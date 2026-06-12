---
title: "Server/Samba Upgrade Now Requesting User and Password When Accessing Shares"
date: 2016-09-28
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2016-09-28
Hi.  So I just updated my server that was running 12.04 to 14.04 then 16.04 in the past 2 days. Everything seems to be working fine except samba.  It works and is accessible from other network computers (which are also Ubuntu machines but now requests username and password to access the shares.  I am using a smb.conf that I've used for years without issue. When using gvfs-mount smb://[share address] (which I use as part of a script when booting one of my laptops) it now says "password required for share ..."  I have purged samba and samba-common then reinstalled both without luck.  I've read that password/security has been upgraded/changed since samba 4, what am I missing that has changed?  Your help would be greatly appreciated!  Thanks!  Here is a copy of the smb.conf:

```

[global]
    workgroup = OURHOME
    netbios name = dkkFileServer
    server string = Samba Server %v
    auth methods = guest
    security = user
    map to guest = Bad User
    domain master = Yes
    preferred master = Yes
    wins support = Yes
    veto files = /Thumbs.db/thumbs.db/desktop.ini/Desktop.ini
    printing = bsd
    printcap name = /etc/printcap
    load printers = yes
    log file = /var/log/samba-log.%m
    lock directory = /var/lock/samba

[Home]
    path = /home/
    read only = No
    guest ok = Yes
    public = Yes
    force user = david
    force group = david

[Storage Drive]
    path = /media/Storage Drive/
    read only = No
    guest ok = Yes
    force user = david
    force group = david

[Music]
    path = /media/Storage Drive/Music/
    read only = No
    guest ok = Yes
    force user = david
    force group = david

[Movies]
    path = /media/Storage Drive/Movies/
    read only = No
    guest ok = Yes
    force user = david
    force group = david  
```

---

### Post by TheFu on 2016-09-29
Can't help with samba, but why would you use it between Unix systems?  Samba really should be used only for Windows clients.

Use NFS. It is the way that Unix systems are meant to share storage. It is faster AND provides native directory/file permissions. No surprises.

Plus it avoids the gvfs (crap-o-la) which are very slow and don't play nice with other programs. 

Do yourself a favor. Use NFS ... and if any of the clients are connecting over wifi, be sure to use soft-mounts and autofs.

---

### Post by wewantutopia on 2016-09-30
Thanks for the reply.  I'll have to check into NFS for the Ubuntu systems, sounds pretty great.  I use gvfs to mount the shares post boot (no fstab) using a script that only mounts them if I'm connected to certain wifi networks.  Can NFS and samba run side by side?  I do still have Windows systems that OCCASIONALLY connect to the network and a few a few Android apps that I use quite often that use SMB plugins so I would still need to use samba.

Help with my issue would still be greatly appreciated.  Thanks!

---

### Post by TheFu on 2016-09-30
Use **autofs** for any mounts that you don't want until requested.  nfs and cifs and other mount systems work with autofs.
NFS and samba don't conflict. The same storage can be shared both ways and accessed concurrently. NFS file locking is well-proven.  I've posted help to others here about using nfs. Look for those threads if you get stuck; there is a trick to getting the mount location to be what you desire. It doesn't work how you think it should. The Ubuntu autofs page is longer than necessary for a simple home network. It has lots of capabilities, thus the length.  

Really there are just 3 things.
a) uid/gid across all the systems need to match. Since data storage is usually shared, that means normal userids. In a home, that is easy.
b) edit the /etc/auto.nfs file
c) edit the /etc/auto.master file (point at the auto.nfs file)
Restart the autofs service. Done. Be happy.
Obviously, you need to install nfs-server and autofs.

For android, use sftp, not cifs.  Heck, setup a NextCloud/Owncloud solution if you want it even easier, but you'll probably want a full VPN. HTTPS isn't really secure - just sayin'.

A few recommendations.
1) don't let shares have spaces or funny characters.
2) never use /media for storage you mount/control.  That is where Ubuntu-managed mounts go.  Don't use /mnt/ for anything that isn't admin and temporary. Keep storage that you've mounted/control separate to prevent conflicts.
3) It is strange to need to "force user" and allow guests.  I've never used either.
4) Always use Unix/Linux file systems for shared storage. Do not use NTFS/FAT-whatever.

---

