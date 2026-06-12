---
title: "NFS mount problems"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by phillhs on 2008-05-13
Hi,

Using Hardy server.

I am experiencing the following problem trying to use automount with nfs shares exported by our other linux machines, I have tracked this to being a problem with /sbin/mount.nfs not detecting that an export is not exported to us.

Our SuSE 10.2 server is protein, and exports are as follows (only 2 listed for example).

/home   daria(rw,no_root_squash,async)
/other  daria(rw,no_root_squash,async) quinn(rw,no_root_squash,async)

The Ubuntu server box is quinn, and as can be seen from the above should not be able to mount protein:/home but should be able to mount protein:/other.

Attempting to mount protein:/other yeilds the following :-

root@quinn:~# mount.nfs protein:/other /mnt -v
mount.nfs: timeout set for Tue May 13 17:26:05 2008
mount.nfs: text-based options: 'addr=xxx.xxx.xxx.xxx'
protein:/other on /mnt type nfs

So the mount succeeds and ls /mnt produces a correct list of files.

However attempting to mount protein:/home yeilds :-

root@quinn:~# mount.nfs protein:/home /mnt -v
mount.nfs: timeout set for Tue May 13 17:27:35 2008
mount.nfs: text-based options: 'addr=xxx.xxx.xxx.xxx'
mount.nfs: text-based options: 'addr=xxx.xxx.xxx.xxx'
mount.nfs: text-based options: 'addr=xxx.xxx.xxx.xxx'
mount.nfs: text-based options: 'addr=xxx.xxx.xxx.xxx'

above repeated several times and then times out

Looking at the /var/log/messages file on protein, it is correctly refusing the mount from quinn :-

May 13 17:27:00 protein mountd[3874]: refused mount request from quinn for /home (/): not exported

So the problem looks to me like mount.nfs is not detecting that the mount request is being refused and is continuing to try and mount the share, which is of course eventually failing.

I suspect that it is not a problem with protein as other Linux systems on our network when atempting to mount protein:/home return imediatly with a failure message.

I can work around this for the time being by manually mounting the shares that I need, however I would eventually like to get autofs working correctly.

Does anyone have any hints as to what can be done to resolve this  or is this a bug with the current version of mount.nfs ?

Cheers,

Phill.

---

