---
title: "ubuntu and virtual box shared folders"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by nshailesh on 2009-02-06
I have installed ubuntu on windows using vbox.
I have some folders shared .
I have installed guest additions.......

I did mount -t vboxsf sname mountpoint as the super user but it gives an error

/sbin/mount.vboxsf : mounting failed with the error : protocol error

---

### Post by konqueror7 on 2009-02-07
did you create a mount folder first? if not...

type in the terminal...
```
sudo mkdir /media/MyMountFolder
```

now mount the shared folder...
```
sudo mount -t vboxsf MySharedFolder /media/MyMountFolder
```

you should be able to locate the shared folder now in the directory...

---

### Post by nshailesh on 2009-02-07
I have already created a folder for mounting...............

The error is something like this

sbin/mount.vboxsf      protocol error

what does this error mean ?

I can mount the folders now.
The problem was with a particular folder which is fine now.

Thanks

---

### Post by TinkerJ on 2009-02-09
I got this error when I was inside the /mnt/sharename directory when trying to mount on /mnt/sharename. As soon as I moved one directory up, things worked fine.

---

