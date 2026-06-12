---
title: "Permissions Problems with Network Shares"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by lightnb on 2007-06-12
I have a computer running "SME Server 7" as a network file server. It has a user called admin with a password. When I access the share from any Windows computer using the admin username and password, I have full access to do anything on the share I want.

When I try to access it from my Kubuntu Desktop, Using the same admin user name and password, I can read files and write to the base share, but If I try to move *some* local folders to the server share I get the error:

> Could not enter folder smb://sharename/[folder_i_tried_to_copy]

Some folders copy fine, some simply don't. I can't see any pattern to which folders i can copy. The permissions on them are all the same. There all coming from my local users home directoy.

I tried doing the same thing as root, but still had problems.

Any thoughts on this?

---

### Post by dmizer on 2007-06-13
try mounting the share using the directions in the second link of my sig.  if that still does not solve your permissions problem, then please feel free to post in the thread and i'll be more than happy to attempt to help you solve it.

---

