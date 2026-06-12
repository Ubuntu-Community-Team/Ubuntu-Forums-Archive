---
title: "mount.nfs"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by roboa1983 on 2008-06-24
I just got an Iomega Network Harddrive. When one tries to make new files, one is given the option of the file type. It seems CIFS is the default. When I try to mount the file with

```
sudo mount -t cifs -o username=guest, password=guest //IP.IP/file /media/nfs
```

it works to a certain degree. I can read and write only with using sudo.

I've tried to mount the file using nfs (and also trying to find solutions). 

```
sudo mount IP.IP/file /media/nfs
```

I've done this because those were possible solutions I had found online. What strikes me is that nowhere do I need to input my name and password, which I guess was necessary in the first case.

Any pointers would be great

Thanks

Roberto

---

