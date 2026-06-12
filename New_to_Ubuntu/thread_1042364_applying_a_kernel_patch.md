---
title: "applying a kernel patch?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-01-17
how do i apply a kernel patch?

I followed the directions on [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I download the kernel from wget -c [http://kernel.org/pub/linux/kernel/v...2.6.28.tar.bz2](http://kernel.org/pub/linux/kernel/v...2.6.28.tar.bz2) to /usr/src with sudo priv

then also with sudo priv in /usr/src tar -xvjf linux-2.6.28.tar.bz2 && rm -rf linux && ln -s /usr/src/linux-2.6.28 linux && cd /usr/src/linux

then i download the patch from wget -c [http://www.kernel.org/pub/linux/kern...tch-2.6.28.bz2](http://www.kernel.org/pub/linux/kern...tch-2.6.28.bz2) I&#7743; in /usr/src/linux when i download it I&#7743; using sudo pri. then still using sudo priv in the /usr/src dir where I downloaded the patch i do bzcat patch-2.6.28.bz2| patch -p1 and get

root@bermudez:/usr/src/linux# bzcat patch-2.6.28.bz2| patch -p1
patching file .mailmap
Reversed (or previously applied) patch detected! Assume -R? [n]

what am I doing wrong? why does the patch not work? do I need it? It that why it is not working because I do not need it?

---

### Post by ibuclaw on 2009-01-17
You can ignore applying the patch.

The patch is only used to update the source-code of previous kernel version.

Regards
Iain

---

