---
title: "Mounting an internal drive as NFS"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by cregy on 2014-01-04
Hi

I have just set up an ubuntu server to share files, videos, music and photos. It has an internal 250gb drive upon which as stored photos and files and an internal 1tb drive upon which is stored music and movies. I have installed the nfs programme as directed by various help files but get stuck on mounting a drive or folder that is not located in my home folder. Could anyone advise me on how to do this please?

Huge thanks

Rich
Youth Worker
[http://wild-woods.org.uk/](http://wild-woods.org.uk/)

---

### Post by r3dd on 2014-01-04
This is the tutorial I used.

[http://tutorialforlinux.com/2013/10/29/linux-kubuntu-how-to-share-files-over-network-with-nfs4-easy-guide/](http://tutorialforlinux.com/2013/10/29/linux-kubuntu-how-to-share-files-over-network-with-nfs4-easy-guide/)

The folder I associated with the shared file was /home/<storage folder>

The changes I made to the instructions to suit my needs were:

```
In the exports file: /exports/<mount folderr>
mkdir /exports/<mount folder>
cd /exports
mount --bind /home/<storage folder> ./<mount folder>
```

The set the fstab to
```
/home/<storage folder>     /exports/<mount folder>      none     bind
```

You can adjust the instructions depending on where you place the folder. Also, make sure you set the storage folder to read/write/execute so that it can actually be used.

---

