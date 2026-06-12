---
title: "Invisible files on NFS mount after update"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by wkuhns on 2014-01-08
I have a server running 3.2.0-58-generic #88-Ubuntu SMP (64 bit). It's configured with nfs-kernel-server. Among other clients, it provides NFS shares to a number of embedded systems running a very stripped down Linux with a 2.4 kernel. I'm an embedded system developer and I've been running this way for many years, over a long series of servers. Today, I have a bizarre problem.

After installing updates to nfs-kernel-server and other packages yesterday, my embedded clients can mount the NFS shares successfully, can copy files to and from the shares, but they **can't display any files**. Scripts which depend on reading directories don't work. The files are there, just 'invisible'.

NFS shares to other more modern clients (Ubuntu 12.04 and 12.10) work fine.
There are no permission problems on the embedded clients. The mount succeeds, and I can read and write files. I just can't see them.

After the update, the current version of nfs-kernel-server is 1:1.2.5-3ubuntu3.1.

The example below is from a console session on one of the embedded clients (they all act the same way). You can see the mounted NFS filesystem. I can create a file on it and read the file, but a directory listing shows nothing. There are actually dozens of files in the mounted directory.

Any idea what's going on? This is a pretty unworkable situation. Thanks for any ideas or suggestions.

```
$ mount
/dev/root on / type yaffs (rw)
none on /dev type devfs (rw)
proc on /proc type proc (rw)
192.168.1.10:/home on /mnt/copper type nfs (rw,v3,rsize=32768,wsize=32768,hard,udp,lock,addr=192.168.1.10)
$ ls /mnt/copper
$ echo "test" > /mnt/copper/test.txt
$ cat /mnt/copper/test.txt
test
$ ls /mnt/copper
$ 



```

---

### Post by wkuhns on 2014-01-20
Anyone? Still having this problem. Short summary:

Ubuntu NFS server with multiple clients. 
'Normal' clients work fine. 
Embedded clients can mount shares and access files, but can't see files.

---

### Post by Zhivargo on 2014-01-20
That looks like a bug. So you might not be crazy. What do you mean when you say normal clients? Best bet would be to revert the server

---

### Post by Zhivargo on 2014-01-20
Can you 
```
vlc <somefile>
```?

---

### Post by wkuhns on 2014-01-20
Normal clients means other relatively modern linux machines. I'm typing this on a client running xubuntu 12.10, for instance. It mounts the same file system from the same server as the embedded systems, but it works fine on this machine. 

Zhivargo, what's the relevance of running vlc? I think that's videolan client - not available on the embedded systems, and I don't see what it would tell me. On the affected clients, I can use (edit, cat, execute) any file if I know the exact path. Can't do a directory listing, though.

I might have no choice but to revert.

---

### Post by SeijiSensei on 2014-01-21
What are the permissions on the exported share and on the mount point?  Being able to display files in a directory but not list them can occur when the directory does not have the "execute" permission set.  You appear sufficiently knowledgeable that this is probably not the answer, but sometimes it's the little things that get overlooked.

---

### Post by wkuhns on 2014-01-23
SOLVED! There is some incompatibility between the very old NFS client version and the new server version. Specifying 'nfsvers=2' on the client (in the mount options) solves the problem.

---

