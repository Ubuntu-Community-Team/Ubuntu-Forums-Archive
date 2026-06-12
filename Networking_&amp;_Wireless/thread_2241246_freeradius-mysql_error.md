---
title: "freeradius-mysql error"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by manickaselvam on 2014-08-25
Hi,

I'm installing freeradius in UBUNTU 14.04 LTS... I did "apt-get update" before installing the freeradius. But even with repeated tries i'm getting the following error...

Setting up freeradius-mysql (2.1.12+dfsg-1.2ubuntu8) ...
reload: Unknown instance: 
invoke-rc.d: initscript freeradius, action "force-reload" failed.
dpkg: error processing package freeradius-mysql (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 freeradius-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)




I did try the following to completely uninstall & re-install

$sudo apt-get purge freeradius-common freeradius freeradius-mysql
$sudo apt-get install freeradius-common freeradius freeradius-mysql


but with no success... 

any help is highly appreciated.

Thanks.

-Manick

---

