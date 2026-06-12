---
title: "[SOLVED] NFS, can mount RW etc, but no access to &amp;quot;sub-mounts&amp;quot;"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by brendanpiater on 2008-08-15
Hi All,

I'm stumped, I have an Ubuntu machine running some NFS shares for me. I can mount these NFS shares with r/w no problem from my laptop, also running ubuntu. However on the "server" I have some additional disk space mounted in this shared folder, say "../media/TV" has a drive mounted in there for my recorded TV. I can see and access "media", the NFS share, but not "media/TV" the sub folder with the extras drive mounted to it. Just blank, nothing. On the actual server it's works fine and via Samba.

I'm presuming it's a permissions thing at some point but no idea where/how adn suspect I'm searching for the wrong terms.... 

Any help would be very helpful.

Thanks in advance.

Cheers
B

---

### Post by kidders on 2008-08-17
Hi there,

> **brendanpiater said:**
> I can see and access "media", the NFS share, but not "media/TV"That's by design. You can't use a single line in /etc/exports to share more than one filesystem.

You can share /media/TV by adding it to /etc/exports as well.

---

### Post by brendanpiater on 2008-08-17
Thanks, much appreciated.
Cheers
B

---

