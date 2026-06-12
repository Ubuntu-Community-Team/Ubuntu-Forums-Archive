---
title: "server 10.04 hangs on reboot"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by billo4th on 2011-01-13
I am new to ubuntu/linux. I decided to build an ubuntu server to replace a failed Win2000 file server. I am having a power issue I need to resolve which is causing the
box to reboot unexpectedly. Upon starting it displays the following:
 
fsck from util-linux-ng 2.17.2
/dev/sda1 was not cleanly unmounted, check forced
/dev/mapper/ubuntu-art-root: clean, 666619/30138368 files, 76780826/120540160 blocks
/dev/sda1: 211/124496 files (1.9% non-contiguous), 49106/248832 blocks
mountall: fsck /boot [418] terminated with status 1
 
If I press 'S' the machine quickly displays something about skipping then goes to a 
login prompt. I would like to know if the machine can be configured to not need intervention to complete booting, so that the users can resume using the server.
 
Thanks,
Bill

---

### Post by cariboo on 2011-01-13
Boot from the Live CD and run fsck on your raid array, make sure that the command completes before rebooting.

---

