---
title: "cannot unmount NFS share"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Kain000 on 2008-11-11
Hey everyone, 

I've been trying to set up NFS for my lan so I can download files from my server much faster than FTP when i'm at home.     I've followed the directions and mounted the shared folder on my desktop but when I want to unmount the folder it says it's not in my fstab folder and also i'm not root.

I'm not sure what I need to do to be able to unmount it.   when i sudo nautlaus the share doesnt apear to be there.  

here's my fstab folder on the client side machine:

sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
10.0.1.13:/home/sean/Desktop/shared /home/sean/Desktop/shared rw,hard,intr 0 0

going from the shared folder on the server's desktop to the shared folder on my own desktop.

sudo mount 10.0.1.13://home/sean/Desktop/shared /home/sean/Desktop/shared 

works and mounts the folder  (although it also puts anything inside the shared folder onto my desktop aswell.)    but i cannot unmount the volume.


thanks for the help!
-sean

---

