---
title: "LS-XL13B NAS Device"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by cranerja on 2014-01-25
I've had the hard drive named above working correctly and having my computer mount it using the fstab line "//ls-xl13b/share    /networkdrive    cifs  guest,uid=1000,iocharset=utf8    0    0". I changed routers the other day and "sudo mount -a" gives unknown error. I can still mount it through the nautilus gui. Any ideas?

Solved: Turns out the cheap router my isp gave me doesn't do dns.

---

