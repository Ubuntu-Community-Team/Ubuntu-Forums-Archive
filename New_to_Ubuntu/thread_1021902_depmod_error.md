---
title: "depmod error"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jratliff on 2008-12-26
Every time I try to install a package, I get this set of errors. What does it mean? What should I do?

E: linux-image-2.6.27-7-generic: subprocess post-installation script returned error exit status 17
E: linux-image-2.6.27-9-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.27-9-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

The package will install and run, but these errors are worrisome. I believe my Ubuntu 8.10 system is up to date.

Thanks for your help. I tried to find an answer before posting this request.

---

### Post by flanagan on 2008-12-26
If you are booting from a memory stick, this bug report might have some information for you (and a possible workaround): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159)

---

### Post by jratliff on 2008-12-26
Thanks Jim.

I was booting from a 1Tb internal SATA drive. I say "was" because I have since done a re-install and am updating it now.

I had done a WUBI installation with a partition for Linux of 8Gb. I wanted to expand that but because the partition was NTFS, Ubuntu could not find the expanded partition and the disk was getting full. So, I just started over with a Linux native partition and a CD installation.

Presumably the previous errors will disappear with the new installation.

Thanks anyway for your reply.

---

