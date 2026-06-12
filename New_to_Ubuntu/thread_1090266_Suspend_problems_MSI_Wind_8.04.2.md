---
title: "Suspend problems MSI Wind 8.04.2"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by braufrau on 2009-03-08
Hi,

 I've been trying to fix this suspend problem all day and I'm at my wits end.
Finally after trying every variant on pointing resume to swap files and swap partitions I came across the uswsusp solution.

  However, when I run sudo s2disk I get
s2disk could not stat the resume device file. Reason: No such file or directory.

  My config file is

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = resume=/host/ubuntu/disks/swap.disk
splash = y
compress = y
early writeout = y
image size = 482763243
RSA key file = /etc/uswsusp.key
shutdown method = platform

and when I do an ls -l /host/ubuntu/disks/swap.disk (which was created by Wubi BTW).

  -rwxrwxrwx 2 root root 1000000000 2009-03-07 09:05 /host/ubuntu/disks/swap.disk

  can anyone help please?

Samantha

---

