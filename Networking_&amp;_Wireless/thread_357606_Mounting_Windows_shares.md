---
title: "Mounting Windows shares"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by leona on 2007-02-09
Hi there

I've had problems mounting windows shares before [(original thread)]("http://www.ubuntuforums.org/showthread.php?t=268247") I got around this by using a start up script to run the mount commands, this has worked fine, until the recent Samba update.  Now when I start up the mounts are no longer mounted, the startup script is still there, I can run it in terminal and it works fine.

How can I debug this problem, I can mount from the command line fine, works every time, it just Refuses to run at start up?  I don't know where to look, I don't know what log file to check, I don't know what I'm looking for, can anyone help?

I've still got the lines in my fstab file which still refuses to work also.

Drapper 6.06.

thanks.

Edit to add, found another thread which seemed to have the same problem, I think mine issue was caused by not having the sym links to smbmount in my /bin dir, links added, works fine now :)

---

