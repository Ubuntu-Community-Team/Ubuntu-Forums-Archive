---
title: "syncronize network folders"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Naegling23 on 2007-05-24
I have two kubuntu edgy boxes, and would like to syncronize a few folders on them (music, pictures, video) so that I can have access to them on each box, as well as a source of backup.  I use samba to share the folders, is there a utility to automatically keep these folders syncronized?

---

### Post by ruy_lopez on 2007-05-24
rsync will remotely update a directory tree, according to changes made since the last update. Its best used with ssh. One box would act as the master, the other as slave, unless you kept a separate folder (not a samba share), and then used that to update the shared folders. The advantage with that is you could tinker with the un-shared folder without disturbing the access from samba clients. And when you wanted to sync, you would just stop the samba server, perform the sync, and startup samba again. Anyway, this is the command for syncing with a remote folder:

```
rsync -avz --delete-after -e `ssh -c blowfish -ax` /local/master remotehost:/share
```

and if you wanted to update locally a share from a local master folder:
```

rsync -avz --delete-after /local/masterfolder /local/sharefolder
```

When you move a file or folder in the master folder, say from one subfolder to another, rsync typically copies it, then deletes the one in the old location. --delete-after, informs rsync to only delete the old ones after all the new ones have been created, that way if the sync fails mid-way through moving the contents of a folder, you wont end up with half the files in one place, and half in another.

You'll have to set up a ssh server on the remote box, before you can run the remote version of the command.

The reason I mention stopping the samba server is, basically, I've never tried rsyncing a share while it was being shared, the results might be unpredictable.

---

### Post by netztier on 2007-05-24
> **Naegling23 said:**
> I have two kubuntu edgy boxes, and would like to syncronize a few folders on them (music, pictures, video) so that I can have access to them on each box, as well as a source of backup.  I use samba to share the folders, is there a utility to automatically keep these folders syncronized?

Check out packages **unison** and **unison-gtk** (GUI variant) from the universe repos. Unison can work over ssh, then you need to have it installed on both systems. In that regard it is similar to rsync. Documentation claims that it's particularly well suited for low-bandwith links.

It can also work with mounted directories. I used to run it over SSH for a long time before changing to synchronising (NFS-)mounted dirs - turned out to be a **lot** faster.

From what I've read and understood about it,Unison assumes a "hub - spoke" topology, where you decide which system is "master" and which is "slave" for a particular synchronisation context - of which you can of course have multiple ones.

best regards

Marc

---

