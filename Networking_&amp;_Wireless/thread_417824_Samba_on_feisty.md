---
title: "Samba on feisty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-04-21
Hi I am experience a problem on feisty upgrade with samba.

I can no longer browse shared folders.

I have a shared folder on the 7/04 machine.

If i go into nautilus -> go -> network and try to access the shared folder i get a "the contents of this folder could not be displayed"

If i try to access the same folder from a windows machine ... i get "group does not exist" error.

This has been since the upgrade to feisty.

Can anyone think what could be wrong here.

Thanks.

---

### Post by sefs on 2007-04-28
Hi, Ive discovered that winbind is causing me a problem on feisty.  It is when this is installed on feisty for me that I cannot browse shares, If i remove winbind I can again browse shares, If i reinstall it ... cannot browse shares, if i remove it again, can browse shares.

Does anyone have a working feisty with samba installed and also winbind.  I would be interested to know how to get this done on feisty.

---

