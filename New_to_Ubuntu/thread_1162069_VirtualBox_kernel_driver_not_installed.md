---
title: "VirtualBox kernel driver not installed?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by radi0j0hn on 2009-05-17
Hi!

I added virtual box using the add/remove tool in Ubuntu and set up the box using "other" as the OS of choice (I'm trying to put in OS/X)

I'm getting this error:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

Can anyone help on this?

Thanks!

John

---

### Post by zvacet on 2009-05-18
Look for these packages in synaptic and install them.Maybe you can try to reinstall virtualbox in synaptic.

---

### Post by XCan on 2009-05-18
I had the same issue even after installing and reinstalling the packages recommended. After taking a look in /etc/init.d I found that I had two files called vboxdrv.dpkg-bak and vboxdrv.dpkg-dist, respectively. The fun part was that, if I ran vboxdrv.dpkg-bak, the problem would be solved. I'm not sure though why they got renamed and why a reinstallation wouldn't put the standard file back.

---

### Post by Joeb454 on 2009-05-18
Try running ```
sudo /etc/init.d/vboxdrv setup
``` Which should setup/install the kernel driver for you.

---

### Post by radi0j0hn on 2009-05-24
Thanks!  I just wiped my PC (including Vista, hooray!) and installed 32 bit 9.04 and all seems OK now.) I was using 64 bit, as I had a processor that would support it, but it seemed to be more trouble than it was worth.

John

---

