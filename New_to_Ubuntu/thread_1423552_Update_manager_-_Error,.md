---
title: "Update manager - Error,"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by RonCosmos on 2010-03-06
Hello this is my first post.

I am using Ubunto 9.10. Everything was going well until Friday when trying to update my my computer. The error I get when trying to use update manager is:

    E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I do what it asks this is what I get.

   ron@Tablet-PC:~$ sudo dpkg --configure -a
[sudo] password for ron: 
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin

My system stalls at this point, there isn't any activity on the hard drive.

At present I can't install any new programs. The system states
   waiting for other software managers to quit.

Any help would be appreciated.

Thank you for your help.

---

### Post by tekkidd on 2010-03-06
I had a problem with dpkg a few weeks ago where it was broken and i could not fix it. Finally after contacting a friend who used debian he gave me a way to "flush" apt and dpkg. Fire up the live cd and mount your HDD then go and delete all the files in:

/var/lib/dpkg/info

Then boot into recovery and fix package errors.

---

### Post by patchwork on 2010-03-06
The waiting for other managers to quit notification generally means you have the gui update manager still running, while trying to use dpkg through the command line.  Make sure the Update Manger is completely closed.

---

