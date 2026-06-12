---
title: "Automount Shared NFS Folders"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by helixed on 2008-01-03
How can I use autofs or autofs4 (or something better) to automount my shared folders on another Ubuntu computer when they are available and to automatically unmount them when they are not in use?

Thanks,

Helixed

---

### Post by DirtDawg on 2008-01-03
I'm not sure you need autofs. I added a line to my /etc/fstab file that looks something like this:
```
555.555.5.5:/Path/To/SharedFolder /media/LocalFolder nfs rw,auto
```
The 555.555... bit is the IP address to the server and it's shared folder.

Then mount with
```
sudo mount /media/LocalFolder
```
or mount all with
```
sudo mount -a
```
and dismount with 
```
sudo umount /media/LocalFolder
```

I'm not sure this is exactly what you're looking for, but this is what I've been doing for quit awhile and it works well.

EDIT: I should mention that the method above will cause the computer to automount on bootup unless the server machine is not on, in which case you'll need to mount manually with one of the mount commands above when it is.

---

### Post by helixed on 2008-01-03
Hey, thanks for the reply.

That's not quite what I was looking for.  My server machine is not always on, and the client tends to be on more than the server.  In order to have it operate effectively, I would basically like my laptop to mount my server when it is accessible, and when I turn off the server computer I would like it to automatically unmount it.  I could use the umount command, but it's kind of a hassle as much as I use it.  

Helixed

---

### Post by DirtDawg on 2008-01-04
Sorry I couldn't be of help. I was in the same position and spent quit awhile working on autofs unsuccessfully, but figured out how to add to fstab and called it 'good enough'. I thought you might too.

Good luck.

---

### Post by helixed on 2008-01-04
Oh well, I guess thanks for the help anyway.

Helixed

---

### Post by chewearn on 2008-01-07
I was searching for an unrelated NFS question; came upon your thread, and immediately afterwards, came upon the answer you seek:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20](http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20)

---

