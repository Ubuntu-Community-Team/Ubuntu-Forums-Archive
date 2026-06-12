---
title: "Autofs and nfs network shares. Path problem..."
date: 2016-05-01
forum: Networking &amp; Wireless
---

### Post by grailswebdev on 2016-05-01
Hi there,

I need some help with a path problem and autofs. Until a few days ago everything worked as expected but out of the sudden the mounting path got magically longer without me changing any configuration neither on the server nor the client.

I used to have the following path on the client to access my nfs network shares:

/nfs/nfsexports/music
/nfs/nfsexports/pictures

Now it's:
/nfs/nfsexports/nfsexports/music
/nfs/nfsexports/nfsexports/pictures

Where does the second "nfsexports" coming from? Can someone tell me what's going on?

Here is my config stuff for the server and clients:

My /etc/exports on the server:
```
/nfsexports       192.168.178.0/24(rw,insecure,no_subtree_check,async)
/nfsexports/music   192.168.178.0/24(rw,nohide,insecure,no_subtree_check,async)
/nfsexports/pictures   192.168.178.0/24(rw,nohide,insecure,no_subtree_check,async)
```

music and pictures are on different hard drives.

On the client I have autofs installed:

/etc/auto.master
```
/nfs   /etc/auto.nfs --timeout=60 --ghost
```

/etc/auto.nfs
```
nfsexports    -fstype=nfs4,rw,bg,intr,hard,rsize=32768,wsize=32768,noatime  192.168.178.77:/
```

Any hints are appreciated.
Thanks.

---

### Post by grailswebdev on 2016-05-05
If someone cares, I found the solution here:

NFSv4 Client -> #4: 
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

> 4. Note with remote NFS paths

     They don't work the way they did in NFSv3. NFSv4 has a global root  directory and all exported directories are children to it. So what would  have been nfs-server:/export/users on NFSv3 is nfs-server:/users on  NFSv4, because /export is the root directory. 

So I simply changed my client settings in /etc/auto.nfs from:

```
nfsexports    -fstype=nfs4,rw,bg,intr,hard,rsize=32768,wsize=32768,noatime  192.168.178.77:/
```

to:

```
nfsexports    -fstype=nfs4,rw,bg,intr,hard,rsize=32768,wsize=32768,noatime  192.168.178.77:/**nfsexports**
```

I still don't know why it happend after the long while it worked perfectly but it doesn't matter now. 
Mission accomplished!

---

