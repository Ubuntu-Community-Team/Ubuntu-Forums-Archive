---
title: "[SOLVED] Can't see subfolders of share with NFS."
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by MetalMusicAddict on 2008-03-28
I have a Share on my NFS server called "Multimedia". On the actual server 2 physical drives are mounted to subfolders of that one. /media/Multimedia/Audio and /media/Multimedia/Video.

I can mount the NFS share "Multimedia" on the client machine and *see* the subfolders, but they are empty.

I normally use SAMBA but am trying to switch. Sharing the root folder this way wasn't an issue in SAMBA so I would have to imaging I could do it with NFS.


My NFS share on the server looks like:
[LIST]
[*]/media/Multimedia 192.168.1.0/255.255.255.0(rw,sync)
[/LIST]
Client fstab:
[LIST]
[*]<serverIP>:/media/Multimedia	 /media/Multimedia  nfs	 defaults   0 0
[/LIST]

Any ideas?

---

### Post by MetalMusicAddict on 2008-03-28
Ok. Looks like all the work was on the server side.

I had to define the sub mounts as well with other options.

Like:
[LIST]
[*]/media/Multimedia 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check,crossmnt)
[*]/media/Multimedia/Audio 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
[*]/media/Multimedia/Video 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
[/LIST]
So if you have your drives mounted in the fstab to subfolders of one you want to share you have to define those in /etc/exports like I have above. The important options were **no_subtree_check,crossmnt**.

---

### Post by Eiríkr on 2008-03-28
You might want to have a look at [post=4541109]this post[/post], where I had some success defining one export and using the "bind" fstab option to mount subdirectories that then appear in my NFS share without the need of separate export definitions.  

Cheers,

Eiríkr

---

