---
title: "[SOLVED] trouble mapping share"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by tlarkin on 2007-12-06
So, I have an extra compaq server lying around, dual xeons, RAID 5, with no OS.  I needed a file server for my graphic design department.

All running Macs, both Macbooks and new intel iMacs.  So, I downloaded and installed Ubuntu on my Compaq server, no issues.  Installed fine.

I used webmin to create a samba share, converted unix users to samba users, mapped the share and this has worked fine for me in the past with the exception that I was using redhat based distros...

When my mac client tries to map it, I get an obscure error message on my mac client and on the samba server logs it tires to connect then errors out with this in the log:

couldn't find service media

I am at a loss

any help be nice, thanks in advance.

---

### Post by tlarkin on 2007-12-06
In the newest version of webmin, under the samba configuration module, under Windows networking options, I set my Samba share to the default service and was able to authenticate.  I can now read and write.

---

