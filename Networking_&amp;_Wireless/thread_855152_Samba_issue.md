---
title: "Samba issue"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2008-07-10
Hi,

So this is the situation - I have two samba shares called local and central. It local and central the create mask and create directory is set to 760 to allow owner and group access to the shared files that will be created.

My problem is that if a user creates a directory of a file in the shares it will get the 760 permissions but the owner and group is set to the user and no no else can access the directory of read the file.

Is it possible to tell samba that if a directory is created in a share it should inherit its group from in parent directory and if a file is created in a directory it should inherit its group for the directory.

If a directory was owned by a group called Accountants and if a file was dropped in by john that he file would have 760 permissions and john/accountants would be user/group.

Rgds
Chris

---

### Post by straps on 2008-07-10
Watch at the **sticky bit**...it's not a samba issue, but a linux issue

bye

---

### Post by chrislynch8 on 2008-07-10
> **straps said:**
> Watch at the **sticky bit**...it's not a samba issue, but a linux issue

bye

I don't follow "The sticky Bit" I've never used it I'l not sure what it is?

Rgds
Chris

---

### Post by straps on 2008-07-10
Sorry, i've confused the sticky bit with sgid...

This could help you..
[http://www.library.yale.edu/wsg/docs/permissions/sgid.htm](http://www.library.yale.edu/wsg/docs/permissions/sgid.htm)

Bye

---

### Post by chrislynch8 on 2008-07-10
> **straps said:**
> Sorry, i've confused the sticky bit with sgid...

This could help you..
[http://www.library.yale.edu/wsg/docs/permissions/sgid.htm](http://www.library.yale.edu/wsg/docs/permissions/sgid.htm)

Bye

Thats exaclty what I was looking for I'll have a better read over it later.

Thanks
Chris

---

