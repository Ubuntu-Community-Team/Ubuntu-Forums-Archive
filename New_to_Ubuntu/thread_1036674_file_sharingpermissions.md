---
title: "file sharing/permissions"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ghostofzuul on 2009-01-11
Got an internal hard drive mounted as per directions i recieved in a post below. Works great, but when i tried to share /media/sdb1 where i created the dir for my back up drive, i get the following message:


'net usershare' returned error 255: net usershare add: cannot share path /media/sdb1 as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = False"
to the [global] section of the smb.conf to allow this.


went into smb.conf... and added the line in the global section, still get the error msg.

thanks..

---

### Post by Solicitous on 2009-01-11
This thread [http://start.ubuntuforums.org/showthread.php?t=825965](http://start.ubuntuforums.org/showthread.php?t=825965) might be of help to you.

---

