---
title: "Any issues with having different Ubuntu versions installed?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by RedMartin on 2009-01-16
I currently have Ubuntu 8.04 and Vista installed on my HDD.

If I install Kubuntu 8.10 to a new partition will there be any issues because I have 8.04 and 8.10?

What will happen with Kernel updates? Will Grub get all confused?

---

### Post by taurus on 2009-01-16
You can have both releases on the same machine.  However, if you installed GRUB from intrepid and you update a kernel in hardy, then you need to edit /boot/grub/menu.lst by hand from intrepid to use the new kernel for hardy.

---

### Post by RedMartin on 2009-01-16
> **taurus said:**
> You can have both releases on the same machine.  However, if you installed GRUB from intrepid and you update a kernel in hardy, then you need to edit /boot/grub/menu.lst by hand from intrepid to use the new kernel for hardy.

I'm not sure I'm following that. Are you saying that I'd have to manually input the kernel details or just that I'd have to put them into the correct order?

---

### Post by taurus on 2009-01-16
Let's try this.

Say you already have hardy installed and now you will install intrepid.  Intrepid will install GRUB to MBR so you can boot intrepid, hardy, and windows.  If there is a new kernel update in intrepid, you don't have to do a thing if you tell the updater to update your bootloader.  But if you boot up hardy and update a kernel, you need to boot back into intrepid and change the entry for hardy in /boot/grub/menu.lst to point to the new kernel in hardy.  Otherwise, you will continue to boot the old kernel when you select hardy from GRUB menu.

---

### Post by Paqman on 2009-01-16
Basically the problem is that Grub is split into more than one place. The first stage(s) live on your MBR, and their job is to point to the partition that has the rest of the GRUB info. That info lives at /boot/grub/menu.lst, and has a list of the various operating systems and where they live. 

So at the moment your Grub on your MBR points to the copy of menu.lst on your Hardy install. If you installed Intrepid it would overwrite Grub on the MBR to point to the menu.lst on the Intrepid partition.

All fine so far.

The problem would occur if you updated the kernel in Hardy. Normally kernel updates automatically change menu.lst so that you boot using the new kernel. However, Hardy would update it's *own* menu.lst, not the one on your Intrepid install that Grub would actually use.

So you'd have to manually change the menu.lst in Intrepid to point to the new Hardy kernel.

---

### Post by RedMartin on 2009-01-17
Taurus, Paqman.

I've got it now. Will have a crack at it later when I'm feeling braver. Thanks for you help.

---

