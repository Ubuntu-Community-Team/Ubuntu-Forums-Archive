---
title: "Change Volume Mounted at /home"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by cfree220 on 2009-03-22
So when I installed Ubuntu, I didn't really understand mount points. I have a large partition dedicated to sharing media between two operating systems. What I want to do is move the current files and folders under /home over to the storage partition and then change the mount point of that volume to /home.

---

### Post by llamabr on 2009-03-23
So tar everything up, move it where you want, untar, then edit your /etc/fstab file.

---

### Post by hyper_ch on 2009-03-23
[http://www.psychocats.net](http://www.psychocats.net) --> Aisyu has written a nice howto for moving one's /home

---

### Post by cfree220 on 2009-03-23
Thank you for the link. I will have to try this after classes today. Just to verify, will I be able to mount an NTFS partition as the home partition? The files need to be shared between Ubuntu and my secondary OS (Vista).

The other concern that I have is whether or not it would be a good idea to move the entire /home folder to a separate partition, or if I should just move the personal folders. Windows has a lot of problems, and a hard shutdown means that I cannot the NTFS volume. Obviously, this could cause some problems with programs that store files in the /home directory. Is there a way for me to move just the Documents, Music, Videos, Pictures, etc folders to the storage volume and then change the default path to those folders?

Finally, if I do move those folders to the storage volume and then lose Windows while that volume is mounted, will I be able to force it to mount from command line?

---

### Post by hyper_ch on 2009-03-23
no ntfs as home

---

### Post by cfree220 on 2009-03-23
:-/

In that case, the second option? Can I move those folders over to the NTFS partition and somehow point programs looking for a file towards that directory instead?

---

### Post by hyper_ch on 2009-03-23
you can symlink the stuff from the home partition to the ntfs one - but the home partition must be a filesystem with unix permissions.

---

