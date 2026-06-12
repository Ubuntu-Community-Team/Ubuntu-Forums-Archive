---
title: "Samba and NT ACL Support"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by ThinkOpen on 2005-07-01
Does anyone know what steps need to be taken to make a Samba Share use ACL's?  Does Ubuntu's kernel come with ACL support built-in?  Basiclly, I want to allow our users to manage permissions/etc from their Windows PCs using ACLs.  I added the following line to the share...

NT ACL Support = Yes

and then ran "sudo /etc/init.d/samba restart"

and the user is still unable to modify the ACLs from Windows... is there something I'm missing?

BTW, the filesystem is ReiserFS

Thanks in Advance.

---

### Post by intangible on 2005-07-01
You will need to enable support on the partition for ACL:

mount -o remount,acl /partition

and just add ",acl" to the "default" or "notail" that's in /etc/fstab to make it perm. 


Remember, the ACLs will look a little different than Windows file shares, but they work fine, I use them.

---

### Post by ThinkOpen on 2005-07-01
OK, that seems to have got ACL's working, however I've got another SAMBA Server question... How to I view open files on a Samba Share?

---

### Post by intangible on 2005-07-01
smbstatus

---

