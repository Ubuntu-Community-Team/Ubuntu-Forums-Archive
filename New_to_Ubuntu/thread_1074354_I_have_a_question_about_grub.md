---
title: "I have a question about grub"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Arehexes on 2009-02-19
Grub for some reason shows I have two ubuntu partitions when I load up grub.  It's like I can pick one partition to go into it, but there is another option for the same one.  Is there a way to get rid of it.  Also is there a wii to connect my wiimote to ubuntu?

---

### Post by mcduck on 2009-02-19
Are you sure that it's two partitions, and not two different kernel versions?

When the kernel is updated the old version is not removed. This allows you to make sure that the new kernel version works fine on your machine before you uninstall the old version. So, after kernel updates, you'll have two (or more) different kernels available in the Grub menu. Uninstalling the old kernels will also remove their entries from the menu.

---

### Post by desm on 2009-02-19
If it really is a duplicate entry you will want to delete it from /boot/grub/menu.lst. 

To open that go into a terminal and type:

> gksudo gedit /boot/grub/menu.lst

or

> sudo nano /boot/grub/menu.lst

Depending upon whether you prefer nano or gedit.

Then scroll down until you find what are pretty obviously the grub menu options. If you're sure one's a duplicate you can delete it. But you gotta be sure!

You best post about the wiimote in another thread.

---

### Post by tarps87 on 2009-02-19
For setting up the wii remove there is a how to here:
[https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)
(I have not tried it yet)

---

