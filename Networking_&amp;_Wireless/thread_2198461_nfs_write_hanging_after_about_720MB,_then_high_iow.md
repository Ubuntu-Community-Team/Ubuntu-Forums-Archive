---
title: "nfs write hanging after about 720MB, then high iowait"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by nashant on 2014-01-08
I'm at a loss. I'm trying to set up nfs sharing on my home server, but as you can guess it's not going well.Reading is fine, but slow (~10Mb/s). Writing starts out at an ok speed (~40Mb/s) but then just dies after about 720Mb. The cpu utilization drops off and the iowait shoots up, sometimes so bad that is causes my system to hang!Exports:/nfsexports     192.168.1.0/255.255.255.0(rw,sync,no_root_squash,no_subtree_check,crossmnt)fstab:server:/        /server      nfs   none     0       0Any help would be GREATLY appreciated!!

---

### Post by nashant on 2014-01-09
Not solved, but after more investigation I described the problem incorrectly

---

