---
title: "Duplicate mounts of SMB shares"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by 5circles on 2007-08-24
I'm not sure if this is networking or a mount issue.

I'm mounting some network shares from the two drives on a Linksys NAS200 into /media.  The two lines in /etc/fstab are as follows:

```
//networkstorage/PUBLIC\040DISK\0401  /media/NAS_drive1  smbfs  credentials=/home/USER/.smbcredentials, uid=guest, gid=users  0  0
//networkstorage/PUBLIC\040DISK\0402  /media/NAS_drive2  smbfs  credentials=/home/USER/.smbcredentials, uid=guest, gid=users  0  0
```

(USER = my username.  The \040s are because it isn't possible to change the name of the main shared drive on the NAS200)

I tested this manually first, and then rebooted to make sure that the mounts would happen automatically.

The mounts happen OK, but 'mount' shows two for each SMB share.  When I try to run umount, I get a message that the drive is mounted multiple times.

I'd like to clean it up, but perhaps there isn't a problem.

Thanks

---

### Post by bernied on 2007-08-24
I've scanned those two lines from your fstab about five times and can't spot a difference. Are they different?

[EDIT]Are you mounting the same share twice with two different sets of credentials? This is new to me, very interesting.

---

### Post by 5circles on 2007-08-24
Whoops - sorry for causing you to take extra time bernied.  I forgot to make the change when copying the two fstab lines.  1 line is for 'PUBLIC DISK 1' the other for 'PUBLIC DISK 2'.

The idea is to mount each drive with the same credentials.  

It probably isn't relevant, but I'm trying to use the Ubuntu box to mirror from one of the NAS drives to the other.  Probably not very efficient, but since the Linksys NAS200 doesn't have this capability I wanted to set it up.  And I'd like to have the Ubuntu box handle it so I'm not slugging one of the Windows systems.

---

### Post by bernied on 2007-08-24
I don't know what is happening either.
Two vague ideas:
- use a different mount directory (try /mnt), just because ubuntu does some clever stuff with mounts in /media that might be causing the duplication
- use cifs instead of smbfs - this has solved some random troubles that I've had with smbfs mounts in the past

And, as you say, it may not be a problem.

---

### Post by 5circles on 2007-08-24
I tried changing to /mnt, but the results are the same.  Here is the relevant section of the output from mount.

```
//networkstorage/PUBLIC_DISK_1 on /mnt/NAS_drive1 type smbfs (rw)
//networkstorage/PUBLIC_DISK_2 on /mnt/NAS_drive2 type smbfs (rw)
/dev/hda1 on /boot type ext3 (rw)
//networkstorage/PUBLIC_DISK_1 on /mnt/NAS_drive1 type smbfs (rw)
//networkstorage/PUBLIC_DISK_2 on /mnt/NAS_drive2 type smbfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

I don't suppose that the order - with the /dev/hda1 in the middle - has anything to do with it.

When I created the new mount points in /mnt I noted that they were 'root root' versus 'root users' in /media.  But they changed to root users when mounted.

The duplicate mounts don't seem to affect what I'm trying to do.  I will try CIFS after the next reboot.  Meanwhile I need to figure out why I'm getting error messages from cp about failing to preserve ownership when doing the remote copies.  Or set up a different backup approach.

Thanks

---

### Post by bernied on 2007-08-25
The failing to preserve ownership thing is to do with samba. When you cp a file, the ownership of the copied file is generally set to be the same as the original. But, when you are copying to a samba file server, the server decides what the file ownership should be, and it will generally be different to the original, so cp will complain. It sounds like your NAS device is not the easiest to modify so you are probably stuck with it.

Have you thought about using tar instead? You can use the --update (or -u) option which will only add new files to the archive.

The double mount thing is weird.

---

### Post by 5circles on 2007-08-25
Thanks for the ideas.  

As you say, the ownership issues probably relate to Samba. I looked at ownership from Windows (where most of the files were copied from originally) and can see that they are owned by the NAS device.  But the authorship (whatever that means) seems to vary from blank to one of the the users.

I wasn't able to get cifs to work yet - still wading through the howtos - so I'm stuck with smbfs for the moment.  I ran into a problem when trying to run the cp for an extended period which makes me question the NAS200 itself.  The connection to the device disappeared mid way through.  And this morning, when trying to mount the drives from the Ubuntu system, I couldn't make the connections until after other activity to it had stopped.   I suspect that it isn't set up very well for multi-tasking, and I have posted a message on the Linksys forums to check with others.  I am reluctant to get rid of it now, in part because I think it will do fine in regular use (rather than the intensity of initial setup).

I'm investigating other backup options, but had thought that, at least in initially while I haven't done research, a file/directory mirror would be easier than tar.   I'm currently using Laplink from another computer, which works OK except for the occasional 'path too long' error that needs to be dealt with.

---

