---
title: "CIFS Mount Shutdown"
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by makitso on 2023-05-17
I am on a wireless network.  
I have an NAS device that I mount via the fstab file listed below. 

 If I use the folder the NAS device auto mounts.  However, if after the device is mount and I do a system restart the shutdown hangs for a long time due to the fact that the network is shutdown prior to the umount. 

If I search the web there a lot of hits that are quite old, suggesting that this problem has been solved.
I have tried adding x-systemd.timeout values to the fstab but there is no change.

So, my question is, what fstab entry would allow for a quick system restart?

Current fstab entry

//192.168.4.205/user /NAS/user cifs credentials=/var/credentials-user,uid=1000,gid=1000,vers=2.0,noauto,x-systemd.automount 0 0

---

### Post by TheFu on 2023-05-17
The systemd.automount kinda sucks.  Use **autofs** instead. [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

autofs is perfect for NAS and USB devices that may not always be available.  Basically, any storage that isn't permanently connected to the computer (i.e. internal storage).

BTW, Win7 machines support vers=2.1.  Win10 and later use newer versions which would aid security and performance.  I don't know which MS-Windows supports vers=2.0 ... Vista?  IDK.

autofs has 2 config files.  auto.master which points at other files based, usually, on the type of file system mounts.  I tend to put NFS mounts into /etc/auto.nfs and cifs mounts into  /etc/auto.cifs.  An example line in auto.cifs:
```
D      -fstype=cifs,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/D
```
The credentials file permissions are this:
```
-rwx------ 1 root root 31 Jan 17  2015 /etc/samba/win7lap-D.credentials*
```
so they aren't easily discovered by anyone.

Of course, if you don't absolutely have to use CIFS, then NFS would be "the Unix way" with much more flexibility and it is pretty easy to get working   either with /etc/fstab or autofs.  Permissions for NFS are standard Unix permissions with owners, groups, ACLs, etc ... I've worked places where almost everything was mounted via NFS, including our HOME directories, so treating NFS storage like it is local almost always works with every program out there.

---

### Post by Morbius1 on 2023-05-17
> I have tried adding x-systemd.timeout values to the fstab but there is no change.

Are you sure you didn't mean x-systemd.idle-timeout

---

### Post by makitso on 2023-05-18
You know, I think the handwriting is on the wall so to speak, I need to move to NFS.  I just did not want to face the learning curve associated with NFS :-(
I have an old Thinkpad that I will test on.

---

### Post by TheFu on 2023-05-18
> **makitso said:**
> You know, I think the handwriting is on the wall so to speak, I need to move to NFS.  I just did not want to face the learning curve associated with NFS :-(
I have an old Thinkpad that I will test on.

NFS works like native, local, storage.  Owners, groups, permissions are all the same as for a local disk.  Mounting is much easier than when using CIFS.  This  assumes that the NAS provides NFS and not just CIFS.

CIFS is still a better option for MS-Windows clients.
For tablets and Android, I use either sftp or a LAN-based cloud server, nextcloud. I copy files over (or have them automatically synchronized).Nextcloud is the 2nd server many people run, after ssh/sftp - even before NFS.  Many NAS devices have a 1-click installer provided for Nextcloud.

---

