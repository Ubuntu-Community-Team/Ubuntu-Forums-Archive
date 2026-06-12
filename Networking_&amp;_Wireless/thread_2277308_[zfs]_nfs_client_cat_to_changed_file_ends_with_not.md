---
title: "[zfs] nfs client: cat to changed file ends with not found"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by joerg4 on 2015-05-08
Hey all.

We get in trouble since an update from our clients from Ubuntu 12.04 to Ubuntu 14.04.

The behavior:

On client A I change an existing file foo on a nfs share.
On client B I do a cat foo.

1st time after mounting it works. cat shows the content of foo. But if I change foo on client A again and do the cat on B I get the error:
cat: foo: No such file or directory

Doing a `ls` on B resolves the problem and `cat foo` works again showing the new content. But if I change foo on client A again the cat on client B wont work.

Analysis:

If a Program on B does the system call "stat" first, everything works. But if a program like cat directly uses the system call open it will not find the file!

With tcpdump and wireshark I can see that Ubuntu 12.04 calls in the NFS paket under "PUTFH" using the correct (updated) filehandle but in 14.04 the filehandle is wrong (equals the old filehandle. before the change on system A).

Now the very interesting part: If my nfs share on the server site resides on ext4 filesystem and I share it over the /etc/exports, the nfs server answers with the error code NFS4ERR_STALE. The client (B) will do a second request with the correct filehandle and everything works fine. Even on 14.04.

If my nfs share on the server site resides on a ZFS filesystem (ZoL 0.6.4.1, CentOS 7 and Ubuntu 14.04) and I share it over the sharefs option or /etx/exports, the nfs server answers with the error code NFS4ERR_NOENT. The client will fail.

Questions:
1. How can I get the newer clients (14.04+) to update the filehandle correctly like on 12.04
2. (Alternatively) How can I get the server to answer with NFS4ERR_STALE on a ZFS filesystem? Or how should the server answer look like according to the specifications?

regards Joerg

---

### Post by joerg4 on 2015-05-20
patched within ZFS on Linux:

[https://github.com/zfsonlinux/zfs/pull/3404](https://github.com/zfsonlinux/zfs/pull/3404)


get the git version and compile it:

git clone [https://github.com/zfsonlinux/zfs.git](https://github.com/zfsonlinux/zfs.git)

---

