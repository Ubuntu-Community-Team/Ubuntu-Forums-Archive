---
title: "Unable to copy files from NFS Host system to Target"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by velman on 2013-10-08
Hello All,

I am trying to bring up a Target board using NFS.  Right now i am not able to transfer files to Target.
I have few more setups where NFS configuration are working. The configuration is as below
Example:
boot loader configuration.
NFS_ROOT = hostip:/home/temp/

if /bin is directory for the Target, then for Host machine it is /home/temp/bin.
Copy files to /home/temp/bin this directory means copying that files into Target.

Problem:
The newly built linux is up on the Target, but the files changed in /bin of Target is not in /home/temp/bin and viceversa.
All the NFS services running. NFS related make menuconfig changes are included in Linux Kernel Compilation.

Kindly, help us to locate what went wrong.

Thanks and Regards,
Velmani

---

