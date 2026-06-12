---
title: "Virtual Box VDI files"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by lledurt on 2011-07-26
I have a corrupt vdi file do to a hard shut down.  My question involves the vdi files.  There seems to be two of them.  There is a ~/..VirtualBox/VDI/WindowsXP.vdi and also a ~/.VirtualBox/Machines/WindowsXP/Snapshots/{6695f7f6-0f53-49c3-9bd1-69bf0b9b361b}.vdi

I am trying to mount the corrupt vdi file using qemu-nbd -c /dev/nbd0 <vdi-file>  This works for the ~/.VirtualBox/VDI/WindowsXP.vdi but it seems to be the original image I created in 2007, not my working image.  I am unable to mount the ~/.VirtualBox/Machines/WindowsXP/Snapshots/{6695f7f6-0f53-49c3-9bd1-69bf0b9b361b}.vdi file.  

My goal is to get some files off the drive and then start over.

Can Anyone point me in the correct direction.
Thanks

---

