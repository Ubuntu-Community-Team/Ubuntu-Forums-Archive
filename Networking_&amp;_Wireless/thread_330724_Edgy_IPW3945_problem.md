---
title: "Edgy IPW3945 problem"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by djh82uk on 2007-01-03
Hi All

I recently decided to give Ubuntu a go, I installed it to my Hard drive, everything is ok except I want to use it with aircrack-ng, so I had to patch the kernel driver and then compile the kernel, I went from 2.6.17 to 2.6.18.3.  It boots ok, and I now have my Senao wifi card working with packet injection via the hostap driver.

However the built in IPW3945 has stopped working since the new kernel, and if I boot the old kernel, it does not work there anymore either.

Please could someone help me?  I have no idea what to try next, I have searched the forum for ages, the kernel recognises the the driver with lspci but lsmod does not come up with anything.

I am fairly new to all this so any help at all would be great

DJH

---

### Post by chintana on 2007-01-17
I can't guarantee this'll work but try this.

Make sure you have a folder called /lib/firmware/`uname -r`.  Check it with ls /lib/firmware/`uname -r`.

If not find out your old kernel version (uname -r) and there should be a folder in /lib/firmware corresponding to your old kernel version.  Create a new folder which correspond to your new kernel version.  mkdir /lib/firmware/`uname -r`.  Then copy all the files from the folder that has your old kernel version to the newly created directory.

Then create the symlink -> ln -s /sbin/ipw3945d-<old kernel version> /sbin/ipw3945d-`uname -r`

Then try doing a modprobe ipw3945

HTH

---

