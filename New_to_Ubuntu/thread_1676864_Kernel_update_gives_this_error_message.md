---
title: "Kernel update gives this error message"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by tednix on 2011-01-27
Just finished using the Software Center to update my system which included a kernel update to 2.6.35-25 for Ubuntu 10.10 32 bit.  When I restarted the system to update the software I get the following error report:

[HTML]Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]I was using Grub Customizer as suggested in a HowTo thread to change my boot order and have the feeling that the Grub file is somehow screwed up, but until now everything was working properly.  I should also mention that Ubuntu is running from a USB external drive and Grub is loaded on that drive.

Hope that someone can help and thanks in advance for any advice.

---

### Post by cariboo on 2011-01-28
it looks more like you have a corrupted package download, I'd suggest opening a terminal and typing:

```
sudo apt-get clean
```

then try the update again.

---

### Post by tednix on 2011-01-28
Thanks Cariboo, but before posting I had tried sudo apt-get clean, autoclean and autoremove.  Prior to the kernel update I was getting the grub EOF message when trying to get Grub Customizer to work.  My reading on all of this is that the new kernel was trying to update the grub boot menu and froze because of something that Grub Customizer controls that I couldn't fix.
Several hours ago I tried to restore from a backup file hoping that the restore would act like a Windows Restore point (which it doesn't) and that program froze as well but not before messing up my Dropbox folders and TomBoy notes.
So finally I just went with a clean reinstall.

---

### Post by cariboo on 2011-01-28
I would have suggested undoing the changes you made with grub customizer, then running update-grub, and retrying the update again, but it's to late now, :)

---

