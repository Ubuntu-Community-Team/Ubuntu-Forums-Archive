---
title: "[Smaba] Unable to write to samba share"
date: 2019-09-15
forum: Networking &amp; Wireless
---

### Post by livelyc on 2019-09-15
Hello,

Forgive me if this is the improper subforum to post this question.  If so,  would an admin kindly move it to the appropriate sub?

I have configured a machine to act as a media server for all my Kodi enabled devices in my home.  I have successfully configured a samba share that is readable from any device on my network,  however I now need those devices to be able to write to certain directories in the share.  for example,  I have configured the server's fstab to mount the following..[INDENT]```
chris@manifesto:/mnt/storage$ ls -l
total 172
drwxrwxrwx 1 hts   video      0 Jun  5 18:56 Artwork
drwxr-xr-x 1 chris chris  53248 Jun 19 17:17 backup
drwxrwxr-x 1 hts   video   4096 Sep 15 13:30 DVR
drwxrwxr-x 1 root  video 106496 Sep 10 18:53 Movies
drwxrwxr-x 1 root  video   4096 Jun 20 19:00 Music
drwxrwxr-x 1 root  video      0 Jun  5 18:03 Netflix
drwxrwxr-x 1 root  video   4096 Sep 15 11:29 repos
drwxrwxr-x 1 root  video   4096 Aug 27 09:38 TV
 
```
[/INDENT]
 
In this example,  I'm SSH'ed into the server and my username, chris, who is a member of the `video` group.  When logged in via SSH, I can read and write to this volume, but when I access the share using SMB protocol, and attempt to write or delete data using the same credentials, I get a permission denied error. It is the same whether I login from Windows,  Another Ubuntu Desktop, or an android device running Kodi.  all are denied write access.

Unfortunately, I'm using a drive that was formatted using NTFS and it contains more data than I can move in order to reformat it to EXT4,  so in my fstab, I was forced to set `permissions` as a means of enforcing user/group policy, as you can see in the following fstab entry for the mount...[INDENT][U][B]
/etc/fstab[/B][/U]
```
UUID=F8428B2F428AF1A4 /mnt/storage ntfs permissions,locale=en_us.utf8 0 0
```

[/INDENT]
if it helps,  Here is my smb.conf file...[INDENT]
_**/etc/samba/smb.conf**_
```

[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
name resolve order = bcast host
dns proxy = no
bind interfaces only = yes
inherit permissions = yes
force user = kodi

# add to the end
[shared]
   path = /mnt/storage
   writable = yes
   available = yes
   guest ok = yes
   guest only = no
   read only = no
   create mode = 0775
   directory mode = 0775
   create mask = 0777
   directory mask = 0777
   force user = nobody
   browsable = yes
   locking = no
   strict locking = no
```
[/INDENT]

If it matters,  the user kodi is also a member of the video group.  I get the same results with those credentials as well. Any advice would be appreciated.

---

### Post by livelyc on 2019-09-15
This has been solved by removing the conflicting `force user` settings.

---

