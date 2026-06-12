---
title: "Adding 32 Ubuntu for 32 bit capability"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-13
I have a 64 bit installation of the Ubuntu 9.04 and would like to add a 32 bit installation. The system is already tri-boot. One 64  bit version of Ubuntu and 2 versions Fedora. So how do I add a 32 bit version of Ubuntu and make it a quad boot system? Can this be done? Or must I remove the 64 bit Ubuntu and then add 32 bit Ubuntu.

Newport_j

---

### Post by dannyboy79 on 2010-04-13
you do it like you would be adding any other OS to you computer. just go and add it. in the partitioning part of the install, tell it you want it beside your existing ubuntu installs or whatever you have to do. you could even do another 64 bit version of ubuntu. it doesn't matter that ones 64 bit and ones 32 bit. when i went to reinstall ubuntu once (same version) it asks me if I wanted to overwrite previous install and install beside it.

---

### Post by philinux on 2010-04-13
> **newport_j said:**
> I have a 64 bit installation of the Ubuntu 9.04 and would like to add a 32 bit installation. The system is already tri-boot. One 64  bit version of Ubuntu and 2 versions Fedora. So how do I add a 32 bit version of Ubuntu and make it a quad boot system? Can this be done? Or must I remove the 64 bit Ubuntu and then add 32 bit Ubuntu.

Newport_j

Just install it as normal to a spare partition. If you have your boot system set up you could install grub to this spare partition, it will complain but thats ok, and let update-grub pick it up. Or let it go and install grub as normal.

---

### Post by J V on 2010-04-13
Just install it the same way you installed the others...

Besides that, 32bit ubuntu won't give you any more compatibility with 32bit applications than 64bit ubuntu will...

---

### Post by QIII on 2010-04-13
Can certainly be done.

But that one disk may be a bit "busy" in terms of partitions.

If you have a spare small drive, it might be worthwhile to add it and install the 32 bit version there.

Just be sure when installing it to watch for the "Advanced" button on the second to last install screen and make sure you don't add GRUB to that installation.

Boot back into your main version of Ubuntu or Fedora and make adjustments to your GRUB/GRUB2 configuration there to get the new version added to you menu.

If you are using Ubuntu as your main OS, boot there and either:

If using GRUB2, run update-grub2

Or

If using legacy GRUB, modify your grub.cfg.

Edit:  Yeah.  What they said.

---

