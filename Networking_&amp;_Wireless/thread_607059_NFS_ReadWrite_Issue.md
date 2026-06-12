---
title: "NFS Read/Write Issue"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by meighty on 2007-11-08
I'm having some issues with my NFS mount. I'm able to mount the NFS share via the fstab with no problems what so ever. I can even see the mount and read the files. I can't however, write to the share. Here is what i have so far. 

Client desktop fstab file:
10.10.10.12:/media/storage      /media/remote_media     nfs     rw,auto  0       0

Media Server fstab file:
/dev/sda1       /media/storage  reiserfs        defaults        0       0


Media server exports file:
/media/storage 10.10.10.11 (rw,sync)


Would this have anything to do with file permission/owner/group of the drive i'm trying to mount and write too? Any thoughts? This is all of course over my LAN and i'm running 7.10. 

Cheers!

---

### Post by meighty on 2007-11-08
Figured it out. Turns out it was file permissions on the folders themselves.

---

### Post by martinsonjr on 2007-11-16
Hello, 

I have the same issue as you had.  Can you please share with me how you figured this out?  What did you set the permissions to in order to make this work?  I really appreciate your help!  I've been working on this all day.

THanks!

---

### Post by meighty on 2007-11-16
If memory serves me correct all I did was change the folders that I wanted to NFS too to be owned by my user instead of root.

So...

sudo chown username foldername
and
sudo chgrp username foldername


Hope that helped.

---

