---
title: "Unable to move home"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by bj218 on 2010-11-21
I am unable to move home to a to another partition called homeu. I have done this in the past but can't do it now what am I doing wrong (see 2 attachments)?

---

### Post by Verbeck on 2010-11-21
here is a good guide [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

looks like you should exclude the .gvfs file

---

### Post by bj218 on 2010-11-21
> **Verbeck said:**
> here is a good guide [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

looks like you should exclude the .gvfs file

What is a gvfs file? I don't know what 1 is & I do not know how to get rid
of it!! Can you tell me how to remove it? Thanks for the guide info. I am going to take a look at it shortly.

---

### Post by Verbeck on 2010-11-21
dunno exactly, but some thing to do with gnome which cannot read by any other user, even root

found this bug
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361)

---

