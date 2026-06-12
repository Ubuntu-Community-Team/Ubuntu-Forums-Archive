---
title: "NAS drive NFS UID setup"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by surfdoc on 2014-08-14
I have a WD my book live NAS drive that I mount via NFS. At present it mounts the files as UID 500 and GID 1000. My client (laptop) settings are UID 1000 and GID 1000. In normal use this is fine as the files have group read/write access. However when trying to syncronise files the uid discrepancy is causing problems. 

I can access the NAS drive via ssh and found the /etc/exports file:


```
# Use guest user (uid 500) for nfs guest.  This is restricted from private
# shares by trustees.
#
/nfs *(rw,all_squash,sync,no_subtree_check,insecure,anonuid=500,anongid=1000)
```

The share is mounted in /etc/fstab as:

```
192.168.0.10:/nfs/Public /mnt/storage nfs auto,user 0 0
```

Running mount shows

```
192.168.0.10:/nfs/Public on /mnt/storage type nfs (rw,user=root,noexec,nosuid,nodev,addr=192.168.0.10)
```


I have tried changing the line in /etc/exports to anonuid=1000 but this doesnt have any effect
I have tried adding a line in /etc/exports specifically for /nfs/Public but this doesnt have any effect

The auto mount is using root as its UID and I presure the all_squash line will relegate the user to a guest user but it doesnt appear to be using the anon setting. By trying to force the UID to 1000 I understand that if another user accessed the share the files would be under my name. This isn't a big problem as I am the only user. 

Am I taking the right approach to this? The most elegant solution would surely be to mount the files to the UID of the current user. However there doesn't seem to be a simple /etc/fstab option to do this for nfs

Cheers

---

### Post by TheFu on 2014-08-14
Why not just change your useid on the client systems to be 500?
Steps:
* use chown -R across the entire file system
* change passwd/shadow/groups files in /etc

It is probably safest to do these things under a liveCD boot, not on the live partitions when logged into the system.

Settings that use userid by name are fine. It is just the settings that use the uid by number that need to be fixed. Shouldn't be many of those.

---

### Post by surfdoc on 2014-08-16
Nice lateral thinking. 

The only issue (I tried your solution by creating a new user with UID=500) is that ubuntu only recognises UIDs over 1000 as normal user accounts (presumably to filter out all the special accounts). This means its doesnt show up on the login page and the top right user menu shows an error message (something like UTF8 invalid). Otherwise it appears to work.

However - reading more about unison and NFS - I seen it suggested that they do not work together at the best of times. The suggestion was to use SSH.

I could do this, but wondered if anyone has experience? 

I have otherwise used NFS as my preferred network drive protocol because I presume it is faster than SSH (my NAS drive also supports afp and smb). If I want to sync then would it be safe to symultaneously log in via ssh for unison or should I create a script to umount the NFS whilst I sync. I guess this would be better as it would prevent any files from being changed whilst the sync is performed.

---

### Post by TheFu on 2014-08-16
Perhaps .... there is a setting that controls the minimal uid number that will be displayed on the login screen?  I think I've seen it for LXDE somewhere under /etc/.  In the old days, I think my uid was 100.  I don't like having any userids show on the login page myself. If you don't know your userid - then you shouldn't be logging in.

I've never used unison. sorry.

---

