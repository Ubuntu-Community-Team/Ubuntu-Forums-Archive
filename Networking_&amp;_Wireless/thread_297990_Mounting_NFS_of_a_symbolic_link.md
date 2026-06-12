---
title: "Mounting NFS of a symbolic link"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by marx2k on 2006-11-12
On my NFS server I have ~/music which I am exporting

Within this folder are 4 symlinks:

marx2k@LivingroomBuntu:~/music$ ls -al
total 8
drwxrwxrwx  2 marx2k marx2k 4096 2006-11-01 03:53 .
drwxr-xr-x 40 marx2k marx2k 4096 2006-11-10 11:08 ..
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:52 collection1 -> /media/hdb4/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:52 collection2 -> /media/hdd3/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:53 collection3 -> /media/hdf2/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:53 collection4 -> /media/hde3/Music


When I mount /home/marx2k/music on the NFS client machine, it mounts the symlinks but that's about it. I can't do anything with them (I cant enter them as directories.) 

For instance:

pigmunch@IlPenguino:~/music$ cd collection1
bash: cd: collection1: No such or directory

Now, if I mount the direct link, bypassing the symlink (if I export the entire /media/hde3/Music for example, it has no problems mounting it as an NFS mount and working with it on the client.

So, bottom line...am I not able to mount symlinks as NFS mounts?? It would be VERY convenient if I could! 

I seem to have no problem working with them from the samba side.

---

### Post by DavidTangye on 2006-11-12
> When I mount /home/marx2k/music on the NFS client machine, it mounts the symlinks
No it does not. You nfs-mounted /home/marx2k/music only, so that point slots into your filesystem at whatever mount point you specified. Then your client side attempts to "navigate" to the symlinks, eg collection1, which is resolved to /media/hdb4/Music ON YOUR machine. This (/media/hdb4/Music) does not exist on your machine, hence the failure.

In contrast, using SMB, the link is resolved onboard and therefore relative to the (SMB) server, and the directory you want is therefore navigated to/displayed correctly.

So there is a fundamentally different way in which SMB and NFS work.

NFS works OK if you want to export this sort of simple set of structures

/dev/hda1 /
/dev/hd.. /usr
/dev/hd.. /home

mount -t nfs servername:/     /mnt/theserver
mount -t nfs servername:/usr  /mnt/theserver/usr
etc

... and then on the server the links are defined as relative, eg, if running the command from the nfs client machine 
> ln ../../../media/hdb4/Music /mnt/theserver/home/markx/music/collection1

ie at /mnt/theserver/home/markx/music/collection1 place a link that goes up three levels then down to home/markx/music/collection1. This link makes sense, ie is navigable from either the nfs server and any nfs client with the mount points I defined above. Note that in this example I have actually defined the symbolic link from the client machine, ie I used /mnt/theserver/home/markx/music/collection1. If I were on the server I would obviously just use the command 
> ln ../../../media/hdb4/Music /home/markx/music/collection1
Both do the same thing: create a symbolic link called collection1 at /home/markx/music on the server, which points to ../../../media/hdb4/Music relative to that point.

Broadly speaking though, SMB is often a better way to go, because of this issue.

---

### Post by marx2k on 2006-11-12
> **DavidTangye said:**
> No it does not. You nfs-mounted /home/marx2k/music only, so that point slots into your filesystem at whatever mount point you specified. Then your client side attempts to "navigate" to the symlinks, eg collection1, which is resolved to /media/hdb4/Music ON YOUR machine. This (/media/hdb4/Music) does not exist on your machine, hence the failure.

In contrast, using SMB, the link is resolved onboard and therefore relative to the (SMB) server, and the directory you want is therefore navigated to/displayed correctly.

So there is a fundamentally different way in which SMB and NFS work.

NFS works OK if you want to export this sort of simple set of structures

/dev/hda1 /
/dev/hd.. /usr
/dev/hd.. /home

mount -t nfs servername:/     /mnt/theserver
mount -t nfs servername:/usr  /mnt/theserver/usr
etc

... and then on the server the links are defined as relative, eg, if running the command from the nfs client machine 


ie at /mnt/theserver/home/markx/music/collection1 place a link that goes up three levels then down to home/markx/music/collection1. This link makes sense, ie is navigable from either the nfs server and any nfs client with the mount points I defined above. Note that in this example I have actually defined the symbolic link from the client machine, ie I used /mnt/theserver/home/markx/music/collection1. If I were on the server I would obviously just use the command 

Both do the same thing: create a symbolic link called collection1 at /home/markx/music on the server, which points to ../../../media/hdb4/Music relative to that point.

Broadly speaking though, SMB is often a better way to go, because of this issue.

Thank you, that was the answer I was looking for.  So, basically, the symlinks that the NFS mounts, even though they are the symlinks in the directory of music on the server machine, the client machine sees them as symlinks to directories on ITS side.  So if I HAD /media/hd*/Music/... on the client machine, this would work, even though it would be pointless to nfs mount that since I'd just make my own symlinks on the client machine.

Ok, that makes sense. That IS pretty unfortunate regarding NFS and the answer here would be to make 4 NFS mounts on the client machine, mount and then symlink them locally on the client machine like they are on the server.

ex: 
$ mkdir /media/NFSMusic1
$ mkdir /media/NFSMusic2
$ mkdir /media/NFSMusic3
$ mkdir /media/NFSMusic4
$ mount -t nfs servername:/media/hde1/music1  /media/NFSMusic1
$ mount -t nfs servername:/media/hde1/music2  /media/NFSMusic2
$ mount -t nfs servername:/media/hde1/music3  /media/NFSMusic3
$ mount -t nfs servername:/media/hde1/music4  /media/NFSMusic4

...and then start making symlinks on the client machine in the local home dir to those /media/NFSMusic* dirs...

correct?

While I agree that using SMB is easier, I kind of wanted to use NFS since I figured SMB was for Linux/Windows communications and NFS is for Linux/Linux - although I guess it seems SMB can also be done Linux/Linux

---

### Post by DavidTangye on 2006-11-12
> So, basically, the symlinks that the NFS mounts, even though they are the symlinks in the directory of music on the server machine, the client machine sees them as symlinks to directories on ITS side.
Sort of. You might find it easier to look at it this way.
Symlinks are jumps to somewhere. NFS mounts are where you import a structure (filesystem or part thereof) across a network. I was explaining before, its best to import whole filesystems not parts, and have symlinks relative in the imported filesystem, so they are still valid when you access them via an imported mount, so this bit ...

> the answer here would be to make 4 NFS mounts on the client machine, mount and then symlink them locally on the client machine like they are on the server.
... is NOT required. Ie you do not need to define symlinks twice: one that fails across a network, and another on the client machine to use instead... that's very messy.

> I figured SMB was for Linux/Windows communications and NFS is for Linux/Linux Not quite true. SMB WAS used by Microsoft for Windows, and IBM for OS/2, but was adopted into the unix/linux world soon thereafter, OK mainly driven by the need to connect to Windows boxes. I know the SMB is considered synonymous with 'Windows Networking' but that is not a helpful generalisation. Ubuntu seems to favour SMB, and not NFS, and to me, that is a reasonably smart thing to do. I use either or both, sometimes simultaneously: NFS for command line and Midnight Commander (even though I used to be able to get it to go through SMB, but lately something in its security seems to be stopping this), and most apps File Save dialogs; but SMB shares as well for Nautilus.

---

