---
title: "can mount but not browse Apple AFP volumes"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by snyperof1 on 2008-04-17
Running Gusty here,

My school newspaper uses Apple servers that I need to access from my Ubuntu laptop. I've installed afpfs-ng 0.8.1 from a .deb i downloaded from their Sourceforge site. using this command:

```
 sudo afp_client mount -u ****** -p ******** servername.com:volume /media/volume

```

login works, and afp_client says it mounts without an error, but when I open Nautilus to browse the newly mounted volume, its a file instead of a directory, and when i try to open it i get a "failure to login" error from nautilus. konqueror and dolphin dont even see the file, even if i unhide hidden files.

so, What am i doing wrong?
Why does the volume appear as i file instead of a folder?
Why cant nautilus log in when afp_client already has?

I found this thread:

[http://ubuntuforums.org/showthread.php?t=138364](http://ubuntuforums.org/showthread.php?t=138364)

but its from awhile back, and they end up talking about problems in fuse, which i dont think apply to me. Thanks in advance for the help.

---

### Post by snyperof1 on 2008-04-18
Ok, well I fixed it.

ran nautilus as root and now i can read and write to the Apple volume using afp.

---

### Post by alexthepuffin on 2008-06-25
By default, running afpfsd will not work when running as one user, but accessing files for another.

A more appropriate way to run this is to run your afp_mount command as the non-root user you intend to use.  

You may also consider putting your afp mount into /etc/fstab, the afpfs-ng docs explain how to do this.

- Alex

---

