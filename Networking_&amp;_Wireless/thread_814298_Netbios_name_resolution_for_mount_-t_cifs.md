---
title: "Netbios name resolution for mount -t cifs"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by dyerseve5867 on 2008-05-31
I'm trying to get a newly installed Ubuntu 8.04 machine on my home network. Apparently, NetBIOS name resolution is working for some parts of the samba suite and not for other parts of it. Specifically when I try to use mount,

sudo mount -t cifs //192.168.1.149/e /mnt/quark/e

works fine, but

sudo mount -t cifs //quark/e /mnt/quark/e

resolves quark through dns instead of through NetBIOS broadcast as windows would, and thus gets the wrong ip address resulting in:

mount error 111 = Connection refused

On the other hand nmblookup gives me:

$ nmblookup quark
querying quark on 192.168.1.255
192.168.1.149 quark<00>

which is correct. Also, smbclient //quark/e works fine, but only after I changed /etc/samba/smb.conf to say

   name resolve order = lmhosts bcast host wins

It seems that mount -t cifs ignores the name resolve order.

Any ideas?

---

### Post by james.king@4act.com on 2008-06-23
You may have figured this out by now, but read this post.

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

By default Ubuntu does not resolve windows hostnames.

---

