---
title: "sudo mount -a fails"
date: 2024-05-20
forum: Networking &amp; Wireless
---

### Post by jimbelknap on 2024-05-20
Hi everyone!  I'm a windows admin (yes I know, boo... hiss....)  and I'm trying to setup a veeam immutable storage box.  I've followed their instructions and keep hitting a fail while mounting a drive, can someone help?  here's a screen shot:


nasadmin@bnnas1:~$ echo 'dev/disk/by-uuid/d2e6092f-6ca3-4552-befb-1395001d76b3 /mnt/veeam xfs defaults 0 0' \ | sudo tee -a /etc/fstab
dev/disk/by-uuid/d2e6092f-6ca3-4552-befb-1395001d76b3 /mnt/veeam xfs defaults 0 0
nasadmin@bnnas1:~$ sudo nano /etc/fstab
nasadmin@bnnas1:~$ sudo mkdir /mnt/veeam
mkdir: cannot create directory ‘/mnt/veeam’: File exists
nasadmin@bnnas1:~$ sudo mount -a
mount: /mnt/veeam: special device dev/disk/by-uuid/d2e6092f-6ca3-4552-befb-1395001d76b3 does not exist.
mount: /mnt/veeam: special device dev/disk/by-uuid/d2e6092f-6ca3-4552-befb-1395001d76b3 does not exist.
nasadmin@bnnas1:~$

---

### Post by deadflowr on 2024-05-20
Incorrect path.
Missing the slash in dev, should be /dev.

---

### Post by oldfred on 2024-05-20
What version of Ubuntu?
Do you have xfsprogs installed?

Post in code tags:
cat /etc/fstab
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

How to use code tags, easier in Forum's Advanced mode editor:
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]
I click on quote icon & edit to code.

---

