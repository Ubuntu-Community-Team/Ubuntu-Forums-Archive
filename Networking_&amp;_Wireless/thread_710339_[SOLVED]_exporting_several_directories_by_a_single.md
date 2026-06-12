---
title: "[SOLVED] exporting several directories by a single nfs mount point"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by robsic on 2008-02-28
I have a large filesystem containing several directories. What I need to do is to share some specific directories (not all of them) by using nfs, and doing so without being forced to create on share per directory.

The reasons behind this is that I have several media files spread across different directories, and want to see them all in one single mount point that the media extender (dvico tvix) can connect to.

This can easily be accomplished with a single Samba share and a couple of symbolic links pointing towards the target directories, but that does not work for nfs, since the client will not follow the server's symbolic links.

Are there any other way to do this? I'm not very pleased by the thought of rearranging the folder structure just because of this, and I rather not using Samba...

Thanks in advance,

Robert

---

### Post by Eiríkr on 2008-02-28
Assuming that your export directory is [font=courier]/export[/font], you could presumably do this by making use of your [font=courier]/etc/fstab[/font] file, adding this onto the end:
```
#
# BIND mounts for NFS shares
#
/data               /export/data    bind  bind  0
/media/share_media  /export/media   bind  bind  0
/home/common        /export/common  bind  bind  0
```
Of course, you'll need to make sure all the destination directories within [font=courier]/export[/font] exist.  Another option might be hard linking instead of symlinks, but I've never used hard links so I don't know how this would go.  But the above bind mounting is exactly what NFS uses on my system.  Then just export [font=courier]/export[/font] and Bob's your uncle.  :)

Cheers,

Eirikr

---

### Post by lloyd_b on 2008-02-28
One possible solution -  use the "--bind" option of the mount command to attach those directories to your NFS directory:
```
sudo mount --bind /home/someuser/share /nfs/someuser
```
will take the "share" directory of "/home/someuser", and mount it on "/nfs/someuser"
I'm not absolutely certain that this will work for NFS (it *should*, but I haven't tested it).  One minor downside is that these mounts will *not* persist across reboots, so you'll probably want to have a script that performs the mounts as part of the bootup process.

Lloyd B.

---

### Post by Eiríkr on 2008-02-28
... or just add the "bind" lines to your [font=courier]/etc/fstab[/font] file.  ;)

---

### Post by robsic on 2008-02-28
> **Eiríkr said:**
> Assuming that your export directory is [font=courier]/export[/font], you could presumably do this by making use of your [font=courier]/etc/fstab[/font] file, adding this onto the end:
```
#
# BIND mounts for NFS shares
#
/data               /export/data    bind  bind  0
/media/share_media  /export/media   bind  bind  0
/home/common        /export/common  bind  bind  0
```
Of course, you'll need to make sure all the destination directories within [font=courier]/export[/font] exist.  Another option might be hard linking instead of symlinks, but I've never used hard links so I don't know how this would go.  But the above bind mounting is exactly what NFS uses on my system.  Then just export [font=courier]/export[/font] and Bob's your uncle.  :)

Cheers,

Eirikr

Hi, and thanks for the replies. I tested to mount the directories using the --bind option in my /export directory, went perfectly ok, everything's there when you look at it at the server. However, when I mount /export from the client, the directories is there, but appears to be empty. Do you use any special options in /etc/exports?

//Robert

---

### Post by Eiríkr on 2008-02-28
Here's a copy of the relevant part of my /etc/exports file:
```
# Zephyrus exports to Odysseus: (mapping requires nfs-user-server)
/export/data    Odysseus(sync,insecure,no_root_squash,map_static=/etc/nfs/Odysseus.map,rw,nohide)
/export Odysseus(insecure,no_subtree_check,no_root_squash,rw,map_static=/etc/nfs/Odysseus.map,fsid=0
```

I've forgotten the specifics, but I think the "fsid=0" part is required for the parent folder of a share.  This config works on my end.  What NFS version are you running?  

Cheers,

Eiríkr

PS -- Might also be the "nohide" for the child directory...

---

### Post by robsic on 2008-02-28
I must have (wrongfully) assumed that it was enough with only one export (/export), and that the mounted subdirectories didn't need to be exported. After applying them as well, and with the nohide option, everything works perfectly fine.

Many thanks :D

Robert

---

### Post by Eiríkr on 2008-02-28
Cool, glad it's working.  I'd actually forgotten that I had them listed in /etc/exports; sorry for not mentioning it.  I confess I don't know why NFS won't export the subdirectories without specifying them, but at least the workaround isn't too painful.  :)

If this solves your issue, remember to mark the thread SOLVED in the Thread Tools dropdown at the top of the page.  

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-03-18
As a bit of a late follow-up --

I've got the [font=courier]nfs-user-server[/font] package installed instead of the Ubuntu-default [font=courier]nfs-kernel-server[/font], as the kernel version does not allow UID / GID mapping.  The user version seems to default to v3, I think, and does not include any v4 functionality from what I can tell.  

Anyway, in relation to this thread, I've found that this version **can** export a single directory into which various other directories have been mounted using the [font=courier]bind[/font] type in [font=courier]/etc/fstab[/font].

Relevant bits from [font=courier]/etc/fstab[/font]:
```
#
# BIND mounts for NFS shares
#
/data  /export/data  bind  bind
/home/user1/Docs/Teaching      /export/Teaching        bind    bind
```

Relevant bits from [font=courier]/etc/exports[/font]:
```
/export         192.168.10.0/24(rw,sync,insecure,no_root_squash)
```

And there you have it -- only one directory exported, greatly simplifying matters.  I'm not sure if this works too with the default [font=courier]nfs-kernel-server[/font] package, and I cannot test that at this time (the two packages are mutually exclusive), but it's worth a try.  

Cheers,

Eiríkr

---

