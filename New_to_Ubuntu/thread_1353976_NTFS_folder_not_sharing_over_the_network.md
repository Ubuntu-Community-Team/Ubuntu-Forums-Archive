---
title: "NTFS folder not sharing over the network"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-13
i've installed Samba and enabled the share including options to allow users to create/delete files. this folder lies in a NTFS partition. however, the users are still not able to open it through a windows machine. any ideas?

---

### Post by quinnten83 on 2009-12-13
Do you get an error telling you that you can only share folders you own?
Nautilus tells me that I need to add "usershare owner only = false" to my smb.conf

---

### Post by Frak on 2009-12-13
Make sure the NTFS permissions are set accordingly, they override share permissions if they are more restrictive.

---

### Post by leprkhn on 2009-12-13
Does this NTFS partition live on a windows box? If so, does this windows box have a restrictive firewall?

---

### Post by rkakkar on 2009-12-14
> **quinnten83 said:**
> Do you get an error telling you that you can only share folders you own?
Nautilus tells me that I need to add "usershare owner only = false" to my smb.conf

ok will try this

---

### Post by rkakkar on 2009-12-14
> **leprkhn said:**
> Does this NTFS partition live on a windows box? If so, does this windows box have a restrictive firewall?

it only has the basic default windows firewall, which has been disabled.

---

### Post by rkakkar on 2009-12-14
> **Frak said:**
> Make sure the NTFS permissions are set accordingly, they override share permissions if they are more restrictive.

how do i check this?

---

### Post by Frak on 2009-12-14
> **rkakkar said:**
> how do i check this?
Right Click -> Properties -> Security

You'll see a list of accounts and their Access Control.

---

