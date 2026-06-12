---
title: "installing new kernel image - worried i'm gonna break something"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by floatingpoint on 2009-01-15
Hey folks,

I'm following a guide to get the Tascam USB-122L working, which is the subject of much discussion over [here]("http://ubuntuforums.org/showthread.php?t=863109") (you'll also find the guide at [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)).

So anyway I get to the bit where I've to install a new kernel

```
sudo dpkg -i linux-image-2.6.25.4-us122l_1.bri_*.deb
```

And I get a big message saying:

>  You are attempting to install a kernel image (version 2.6.25.4-us122l) However, the directory /lib/modules/2.6.25.4-us122l/kernel still exists.  If this directory belongs to a previous linux-image-2.6.25.4-us122l package, and if you have deselected some modules, or installed standalone modules packages, this could be bad.

If /lib/modules/2.6.25.4-us122l/kernel belongs to a old install of linux-image-2.6.25.4-us122l, then this is your last chance to abort the installation of this kernel image (nothing has been changed yet).

If you know what you are doing, and if you feel that this image should be installed despite this anomaly, Please answer n to the question.

Otherwise, I suggest you move /lib/modules/2.6.25.4-us122l/kernel out of the way, perhaps to /lib/modules/2.6.25.4-us122l.kernel.old or something, and then try re-installing this image. 

Stop install since the kernel-image is already installed?   Y / N? 

And that's where it's sitting right now.

I thought the sensible thing to do would be to ask you lot. The fate of my install is in your hands. What should I do?

---

### Post by LowSky on 2009-01-15
you really should only use kernels that are updated through synaptic.

also that kernel is a downgrade, which could break your system
and thos instructions are for Debian, not ubuntu, which while simular are not the same, so it might break your system

---

### Post by floatingpoint on 2009-01-15
One part of the guide is for Debian Lenny. There's a part for Ubunty further down.

---

### Post by floatingpoint on 2009-01-15
I got this output when I tried to unpack the .deb

```
Unpacking replacement linux-image-2.6.25.4-us122l ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.25.4-us122l
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.25.4-us122l (1.bri) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(1.bri was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(1.bri was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.25.4-us122l
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.25.4-us122l.postinst line 1181.
dpkg: error processing linux-image-2.6.25.4-us122l (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.25.4-us122l

```

whats causing this?

---

