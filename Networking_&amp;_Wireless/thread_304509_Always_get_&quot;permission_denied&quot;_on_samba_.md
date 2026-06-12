---
title: "Always get &quot;permission denied&quot; on samba mount"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by theosib on 2006-11-21
I have a samba share (from another Ubuntu machine because I can't get NFS to work either) that always gives me permission denied errors.

Here's what I get when I'm in smbclient:

  afe200206.gz                        A 12899880  Thu Nov  9 15:53:14 2006

                63297 blocks of size 65536. 0 blocks available
smb: \original\afe\> get afe200206.gz
NT_STATUS_ACCESS_DENIED opening remote file \original\afe\afe200206.gz

No matter what I set on the server and no matter what I do on the client, I cannot actually read any files.  On the server, I have basically given everything but write permission to all users, and there is no password.  Still no help.

Can anyone give me some suggestions?

Thanks!

---

### Post by mssever on 2006-11-22
Can't help you with Samba, but I can probably help troubleshoot NFS.

---

### Post by theosib on 2006-11-22
Well, with NFS, all I ever get is "permission denied" when I try to mount the share.

# mount 192.168.111.101://media/cdrom0 /mnt/nfs
mount: permission denied

fstab line:
192.168.111.101://media/cdrom0  /mnt/nfs nfs  defaults,noauto 0 0

# mount /mnt/nfs
mount: 192.168.111.101://media/cdrom0 failed, reason given by server: Permission denied

On the server in /etc/exports, I have:
/media/cdrom0 *(no_root_squash,async,all_squash)

---

### Post by mssever on 2006-11-22
> **theosib said:**
> Well, with NFS, all I ever get is "permission denied" when I try to mount the share.

# mount 192.168.111.101://media/cdrom0 /mnt/nfs
mount: permission denied

fstab line:
192.168.111.101://media/cdrom0  /mnt/nfs nfs  defaults,noauto 0 0

# mount /mnt/nfs
mount: 192.168.111.101://media/cdrom0 failed, reason given by server: Permission denied

On the server in /etc/exports, I have:
/media/cdrom0 *(no_root_squash,async,all_squash)

Here are my values for reference.

/etc/fstab ```
[FONT=Courier New]192.168.1.50:/home/scott/webmaster      /home/scott/webmaster   nfs     rw,hard,intr    0 0
192.168.1.50:/                          /media/scott-desktop    nfs     rw,hard,intr    0 0
192.168.1.50:/home/scott/bin    /media/scott-desktop/home/scott/bin     nfs     rw,hard,intr    0 0
192.168.1.50:/media/EXTERNAL_HD         /media/EXTERNAL_HD      nfs     rw,hard,intr    0 0[/FONT]
```/etc/exports ```
[FONT=Courier New]/                       192.168.1.100(rw,async,no_root_squash) 192.168.1.101(rw,async,no_root_squash)
/home/scott/webmaster   192.168.1.1/24(rw,async)
/home/scott/bin         192.168.1.1/24(rw,async)
/media/EXTERNAL_HD      192.168.1.1/24(rw,sync,no_root_squash)[/FONT]
```You have some unusual syntax. Im not sure whether its incorrect or not. First, in fstab, I only use a single slash. Also, in exports, no_root_squash and all_squash seem to be contradictory. Try using only one. Note that you should restart your NFS server between changes.

Also, NFS uses different mount options than standard filesystems. See the mount man page for details. Theres a section for NFS mount options.

---

### Post by madmorpheus on 2006-12-01
Make sure your samba directory and files give permissions at the linux level to the samba users and groups.

---

