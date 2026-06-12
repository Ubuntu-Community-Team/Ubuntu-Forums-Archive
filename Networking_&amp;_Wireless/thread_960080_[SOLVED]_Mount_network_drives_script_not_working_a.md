---
title: "[SOLVED] Mount network drives script not working anymore"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Sanix on 2008-10-27
Hi,

I had to install Ubuntu 8.10 . Now my network script is not working anymore, although the only thing, which has changed, is the ubuntu version.

> 
sudo mount -t smbfs -o username=xxx,domain=edu,password=xxx //fsemu18.edu.ds.fhnw.ch/e_18_data11$ /media/pub/


The error is:
> 
mount: wrong fs type, bad option, bad superblock on //fsemu18.edu.ds.fhnw.ch/e_18_home11$/daniel.suter,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

