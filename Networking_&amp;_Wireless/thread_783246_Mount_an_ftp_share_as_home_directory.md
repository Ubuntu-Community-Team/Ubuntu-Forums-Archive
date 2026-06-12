---
title: "Mount an ftp share as home directory"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by talz13 on 2008-05-05
I'm in the process of building a new pc for my parents that will (hopefully) be running ubuntu.  I recently upgraded my home network to gigabit and found that samba and nfs are not very capable at these speeds.  FTP, however, works rather well (tested averages: smb: 10-20MBps, FTP: 25MBps+, NFS needs testing still).

If NFS doesn't fit the bill, I would be interested in making their home folders mount via an ftp share as opposed to an smb/nfs share.

Why do I want to have their home folders mounted from a server anyway?  Because the server gets nightly, scripted backups performed every night, and they NEVER back up ANYTHING on their own.  Thus, in the (likely) event that their drive dies someday, everything will be safe on the server's drive, the USB backup drive, and the encrypted truecrypt volume stored on my remote web hosting (which is in a different state than I am).

So, is auto mounting an ftp directory on boot going to be difficult?  I have seen mention of using fusefs or something, but I don't know if that would work for a home directory very well.

---

### Post by nixscripter on 2008-05-05
> **talz13 said:**
> I'm in the process of building a new pc for my parents that will (hopefully) be running ubuntu.  I recently upgraded my home network to gigabit and found that samba and nfs are not very capable at these speeds.  FTP, however, works rather well (tested averages: smb: 10-20MBps, FTP: 25MBps+, NFS needs testing still).


Why don't you think NFS fits the bill? It is true that NFS, in my experience, is not very good for sustained data transfers. However, I would say that is not how a home directory is often used. A home directory, I would argue, plays to a strong point of NFS: a large number of small files (less than 100 MB). This is assuming you're not doing something like video editing. This is because NFS (or at least most implementations) use extensive host side caching; for small files, this gives very low apparent delays, since the actual data commits to be staggered for reasonable throughput over the network.

Having used NFS for a backup server (where hosts dump tarballs in a sustained stream), a log dump server (where hosts dump small logs once in a while), and netbooted diskless clients (where an NFS mount is the root partition), I would argue it is excellent for a home directory. I can also say it is easy to set up at boot with a line in /etc/fstab. Just keep a reliable connection, and don't hard mount it. ;-)

---

### Post by talz13 on 2008-05-06
I suppose nfs wouldn't be that bad for a home directory.  Could you explain about not hard-mounting the share?  I remember something about that from setting up nfs on my mac a long while ago using some automounter or something as opposed to a static mount...

---

### Post by nixscripter on 2008-05-06
To soft mount, just pass it as an option when mounting the filesystem: ```
mount -t nfs -o soft server:/dir mnt-pt
``` And the same thing applies to an entry in /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
server:/dir     mnt-pt          nfs     soft            0       0

```

Hope this helps.

---

### Post by timcredible on 2008-05-06
might be easier to just do a backup on their local machine's drive.  rsync will do that easily, just put the command in /etc/cron.daily to run it every day.  grsync is a gui frontend for rsync.

---

