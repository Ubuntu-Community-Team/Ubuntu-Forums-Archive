---
title: "mount.cifs ignoring uid"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by gstrock on 2005-10-26
I installed Kubuntu 5.10 and my friend Ubuntu 5.10 at work.
Neither of us can mount our shares with write permission.

The problem seems to be that the **uid** argument is
being ignored.  After mounting the files and directories have
uid's and gid's that correspond to the remote file system,
so we can only read them.

My command looks like this and I've tried it as root and
as myself:

mount.cifs //SERVER/eu ~joe/mnt/eu -o username=joe,password=foo,uid=joe

Now what is interesting is this works in the 2.4 kernel when
using smbfs.

I don't know what version of the samba the server is running
but I'm wondering if there is something wrong on the server
end.

- greg s.

---

### Post by mlomker on 2005-10-26
> mount.cifs //SERVER/eu ~joe/mnt/eu -o username=joe,password=foo,uid=joe


I've never used the uid option and my shares are all read/write.  Are you saying that the user account that you are mapping with doesn't have write permissions on the Windows share?  I don't think the smbmount is going to over-ride permissions if that's what you mean.

I've also never used that particular script.  I just use **mount -t smbfs** instead.

---

### Post by gstrock on 2005-10-27
Go here to see what I'm talking about:

[https://bugzilla.samba.org/show_bug.cgi?id=2512](https://bugzilla.samba.org/show_bug.cgi?id=2512)

---

### Post by mlomker on 2005-10-28
That explains it--I use Windows servers and not samba servers.

---

