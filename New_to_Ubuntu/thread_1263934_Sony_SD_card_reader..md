---
title: "Sony SD card reader."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-09-11
Hi guys,

I have a Sony Vaio W series netbook and I am struggling to get the SD card reader to work. 

Output from:
anders@anders-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc98ffefc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

Any ideas anyone?

Cheers. Anders

---

### Post by jimwatson on 2009-09-21
Hi - I was looking at the W series myself, sorry to hear that you're having problems.  I had a Z series laptop until recently and was also unable to get either the SD card or Magic gate working.  The camera required a separate module to get it up and running.

The fdisk command will only show things that are recognised as drives, maybe a more useful command at this stage would be 'lspci' or possibly 'lsusb' to establish what hardware is being used.  Neither of those commands need to be run as sudo.  Please try those and post the results here.

---

### Post by sandyd on 2009-09-21
ouch
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40585](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40585)

---

