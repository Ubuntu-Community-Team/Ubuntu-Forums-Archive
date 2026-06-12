---
title: "advice on mirroring an ftp site"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by occams_beard on 2009-07-26
I need to mirror an FTP site. It has to be a true mirror where files stay in sync. i.e, when a file is removed from the remote server, it gets removed on the local server.  Just trying to figure the best way to do this and so far I've come up with 2 options. 

1. Mount the ftp dir with curlftps, and simply use  rsync. 
2. use "ftpcopy" [http://www.ohse.de/uwe/ftpcopy/ad.html](http://www.ohse.de/uwe/ftpcopy/ad.html)

I can't seem to do option #1 because I need to be able to do this as a non-root user, and I can't mount if I'm not root. Any way around this?

So option #2 seems like a viable solution, but are there any other options that might be better?

---

### Post by Liolikas on 2009-07-26
Curlftps is fuse based so you should not need root for it.

---

### Post by occams_beard on 2009-07-26
When i try to run curlftpfs as a regular user, it complains about not being able to open fuse.conf

```

curlftpfs ftp.whatever.com ~/test_ftp_mount
fusermount: failed to open /etc/fuse.conf: Permission denied

```

So I tried running it as root, but then it doesn't want to mount in my home dir

```

sudo curlftpfs ftp.whatever.com ~/test_ftp_mount
fuse: bad mount point `/home/bob/test_ftp_mount': Permission denied

```

---

### Post by niteshifter on 2009-07-26
> **occams_beard said:**
> When i try to run curlftpfs as a regular user, it complains about not being able to open fuse.conf

```

curlftpfs ftp.whatever.com ~/test_ftp_mount
fusermount: failed to open /etc/fuse.conf: Permission denied

```



Add the user to the fuse group and 
```
sudo chmod g+r /etc/fuse.conf
```

---

