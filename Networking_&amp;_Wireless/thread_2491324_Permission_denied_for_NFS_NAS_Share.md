---
title: "Permission denied for NFS NAS Share"
date: 2023-10-04
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2023-10-04
I was successfully able to mount a NAS (ZyXEL NSA325-v2) to an Asus Chromebox with Lubuntu 22.04 by adding to fstab:

192.168.1.14:/i-data/e6510fdf/nfs/KodiShare /nfs/Volume1 nfs rw,vers=3 0 0

But I noticed that I wasn't able to edit most of the files or folders which showed permission 501. 

So I tried this:

sudo chmod u=rwx,g=rwx,o= /nfs/Volume1

Now I get "Permission Denied" if I try to open a file on the NAS.  Also:

ls -l /nfs/Volume1 

Now doesn't work unless I use sudo (pretty sure that wasn't necessary before).  And then it still shows the files and folders unchanged with permission 501.

How can I make this work so that the NAS is always mounted and I am always able to edit the files and folders?

Any help much appreciated!

---

### Post by TheFu on 2023-10-04
You'll need to lookup information on the specific NFS server that ZyXEL uses, but typcially, the client root/sudo doesn't have elevated permissions to modify anything on an NFS server.  Permissions need to be configured on the NFS server storage.

The "best practice" for using NFS is to have centralized user and group management setup that both the clients and NFS servers use.  This way, the uid and gid will always match between the clients and servers.  If they don't, you get into issues like you seem to be having.

To troubleshoot, you'll need to show the permissions on files and directories from the server-side AND from the client-side to see what's different.  **ls -al** is how to show that for the `pwd`, so be certain to chdir into the same directory on both the server and client BEFORE running the **ls -al** command.

For example, 

From the NFS server:
```
drwxr-xr-x  13 tf jellyfin  4096 Mar 19  2015 Jazz/
```

From an NFS client:
```
drwxr-xr-x  13 tf netdev  4096 Mar 19  2015  Jazz/
```

See how the group is different?  Jellyfin is my normal media server, so for my Jazz music collection, I ensured it was the group, but for playback, any user that has read access to the directory and files below it is fine.

The jellyfin group on the server happens to have the same gid number as the netdev group on this specific NFS client.

While you don't see this, I make certain that all my systems use the same directory locations for storage - local or NFS remote. Helps me keep my sanity.  But my NFS servers are on Ubuntu Servers, so I have complete control over where storage is mounted both with real HDDs and over NFS connections.

Clear as mud?

---

### Post by SnoopFogg on 2023-10-04
Thanks for that...I think I get the principle.  However now when I access the NAS with sudo, it just shows an empty folder.  It's 10 years old and no longer supported so might be time for an upgrade.  

Thanks again

---

### Post by TheFu on 2023-10-04
> **SnoopFogg said:**
> Thanks for that...I think I get the principle.  However now when I access the NAS with sudo, it just shows an empty folder.  It's 10 years old and no longer supported so might be time for an upgrade.  

Thanks again

NFSv3 goes back to the mid-1990s.
NFSv4 is from 2002.

So there's no reason the system shouldn't be able to handle connections from Ubuntu, unless they cut so much of the NFS standard code out as to break it. I don't think ZyXEL would do that, but who knows. They've definitely had security issues over the years. Who knows.

Just get the uid/gid on both systems to match. I'd be surprised if the ZyXEL interface didn't have a way to make that happen.  

Often, the easiest way to solve this would be the create a new directory (or 3) at the top level from the NFS client, the go to the NFS server an look at the uid/gid and permissions for those things. Don't use root, use your normal account to make those directories.

---

### Post by SnoopFogg on 2023-10-06
> **TheFu said:**
> NFSv3 goes back to the mid-1990s.
NFSv4 is from 2002.

So there's no reason the system shouldn't be able to handle connections from Ubuntu, unless they cut so much of the NFS standard code out as to break it. I don't think ZyXEL would do that, but who knows. They've definitely had security issues over the years. Who knows.

Just get the uid/gid on both systems to match. I'd be surprised if the ZyXEL interface didn't have a way to make that happen.  

Often, the easiest way to solve this would be the create a new directory (or 3) at the top level from the NFS client, the go to the NFS server an look at the uid/gid and permissions for those things. Don't use root, use your normal account to make those directories.

Thanks, I tried a new directory but it was still behaving strangley (although differently).  But that gave me the idea to change the permissions for the original directory from read/write to read only, restart the nas, then back to read/write.  After another restart it's all working fine - mounts at startup, no need for root and uid's match.  That's just saved me buying a new nas, so super happy!

---

