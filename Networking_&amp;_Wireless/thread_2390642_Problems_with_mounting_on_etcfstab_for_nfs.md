---
title: "Problems with mounting on /etc/fstab for nfs"
date: 2018-04-30
forum: Networking &amp; Wireless
---

### Post by gueland on 2018-04-30
I have successfully mounted most of my nfs shares of my HP MyCloud.   But, 2 of the shares have apostrophes in the name, which causes them to  not mount.

Example:

ServerName:/mnt/HD/HD_a2/Name's /nfs/Name nfs auto 0 0

Can you help?  I have tried putting 047 for the apostrophe in the name (Name\047s) but that did not work.

Running Ubuntu 18.04 on a Dell Inspiron 518.

---

### Post by SeijiSensei on 2018-05-01
Can you not change the name on the server itself?  That apostrophe will just cause you endless trouble down the road.

Sometimes doubling the apostrophe works, i.e., Name''s.

---

### Post by gueland on 2018-05-01
Tried doubling the apostrophe, did not work.  Putting quotes around it did not work either.

---

### Post by SeijiSensei on 2018-05-01
How about just escaping it normally with the backslash like Name\'s?  I still think you solve the problem at its root and get rid of the apostrophe on the server directories.

---

