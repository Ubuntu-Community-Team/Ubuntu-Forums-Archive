---
title: "mounting samba with a wireless connection"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by HereInOz on 2008-11-08
Hi All,

For some while now, I have been running various releases of Ubuntu on my laptop, using a wireless connection, and mounting a samba share from another machine at log on, using the appropriate entry in fstab to achieve it, namely:

//server/share /path/to/mount/point smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user   0  0.

I have checked the credentials file and it appears OK.

Up until now, this mount has worked as soon as the wireless connected, but with Intrepid, it does not mount until I do a "sudo mount -a" in a terminal.  Then all is well.

Has there been a change in the way that Intrepid deals with fstab, and is there anything I can do to make the samba mount occur when the wireless connection is made.

At the moment, it appears as though the system tries to mount the samba share, can't find it because at the time there is no network, so just gives up and doesn't try again.

I hope someone can assist with this one.

---

