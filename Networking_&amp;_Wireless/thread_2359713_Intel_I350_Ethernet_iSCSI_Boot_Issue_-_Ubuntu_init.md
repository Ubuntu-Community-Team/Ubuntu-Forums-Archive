---
title: "Intel I350 Ethernet iSCSI Boot Issue - Ubuntu initrd cannot found the iscsi drive"
date: 2017-04-26
forum: Networking &amp; Wireless
---

### Post by hogifozi on 2017-04-26
Hi all,
 
I'm trying the iSCSI Boot by the Intel i350 NIC card.
The content inside the iSCSI LUN includes kernel, initrd and grub config (/boot) only.

The kerenl and initrd is copy from a machine which is installed by Xubuntu 16.04 LiveCD on a local drive.
The version of Linux kernel is '4.4.0-28-generic'.


The card has the agent ROM and can connect to my iSCSI target server by 'Primary iSCSI'.
All work fine in Grub2 menu.
I can use 'ls -l' in Grub2 shell to see my iSCSI LUN as a local disk.


But, when I boot into initrd, the command 'blkid' cannot see any iSCSI drive shown in Grub2.
The initrd doesn't have kernel module 'iscsi_ibft'.
 
Is module  'iscsi_ibft' necessary for booting from iSCSI target?
Is module  'iscsi_ibft' necessary for booting via Intel Ethernet iSCSI Boot?
Does the iSCSI drive act as a local drive when initrd scan the scsi bus?


Thanks.

---

### Post by wildmanne39 on 2017-04-26
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by hogifozi on 2017-04-26
Sorry. The 'remove format' is applied.

---

