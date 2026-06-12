---
title: "iSCSI help needed"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by banditti on 2007-05-23
I have configured open-iscsi and it works.  Now how do I mount a lun?  

iscsiadm -m node
iqn.1992-08.com.netapp:sn.84169913

---

### Post by banditti on 2007-05-24
Anyone?

---

### Post by Yann2 on 2007-05-29
Up, same problem here /o\ :(

---

### Post by Yann2 on 2007-05-29
Ok, found it. You have to what they call  "log in":

root@mirror:/mnt# iscsiadm -m node -T iqn.2001-05.com.equallogic:6-8a0900-ad3cb3a01-50300006eb14639e-mirror1 -p 192.168.20.34:3260 -l

And then you can see with: 

 iscsiadm -m session

if you are correctly logged in or not. That should create a device file named /dev/sdb (or maybe another name for you), which you can then mount in the fstab like described in the man.

---

