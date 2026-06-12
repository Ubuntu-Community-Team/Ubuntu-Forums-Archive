---
title: "How do I include a netboot option in Grub gfxboot"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by kaivalagi on 2008-02-28
I am about to install LinuxMCE on a HTPC on my home network. To pre-empt this I am trying to figure out how to add an extra boot option on my existing ubuntu install on another pc, so I can netboot a media director instead of booting my standard install.

I started by adding the following to my menu.lst:

title 		LinuxMCE Media Director
dhcp
root		(nd)
kernel		/tftpboot/100/vmlinuz ramdisk=10240 rw root=/dev/nfs boot=nfs nfsroot=192.168.0.1:/usr/pluto/diskless/100
initrd		/tftpboot/100/initrd.img

Although the destination is not there yet (will be very shortly) I wanted to ensure the boot option would atleast start off a networking process. However when trying the option I get an error as grub doesn't understand the (nd) option.

Does the default grub installed in Ubuntu not have netboot support?

If I am running gfxboot how can I add this feature to it?

I really don't want to have to go into my BIOS and enable a netboot each time I want to access my media remotely, can anyone provide me with a little background on this feature of grub, and pointme in the right direction?

So far from what I have skim read, it seems like I may need to re-compile grub with options for booting over the network, is this true? If I have to do this what will this mean fin relation to gfxboot?

Any pointers anyone? This is all new territory for me :)

---

### Post by kaivalagi on 2008-03-18
bump

anyone?

---

### Post by kaivalagi on 2008-03-30
Does anyone know if the default grub installed in Ubuntu have netboot support or will I need to re-compile? Has anyone gone through this process of netboot/pxeboot in Ubuntu 7.10?

Just some simple answers will do, I don't want to have to start messing with grub installs unless I really have to...if I have to then I will start reading up on the subject in more detail...

Anyone?

Thanks

---

