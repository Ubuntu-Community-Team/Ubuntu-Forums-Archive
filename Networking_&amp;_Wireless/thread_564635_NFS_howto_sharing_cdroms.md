---
title: "NFS howto sharing cdroms"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by dannytherocker on 2007-10-01
Hi, altough I've been using Linux for almost 2 years, today I wasn't able to share cdrom, from a server to my laptop:

on server's /etc/exports this should be the line:

```
/media/cdrom 192.168.1.1/24(rw,sync)
```

on client's /etc/fstab this should be the line:

```
192.168.1.1:/media/cdrom /mnt/disk nfs ro 0 0 
```

It all doesn't seem to work.../mnt/disk appears to be full...but all the files are unreadable....(e.g. a file .vob is seen by the system as a .txt)

Where's my error ??

---

