---
title: "Managing CIFS share and multiple users on same box"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by dewarrn1 on 2016-09-15
Hi all,

     I have a CIFS share provided by a FreeNAS box that is accessed by multiple Ubuntu desktop machines (and for the record some Windows boxes, too).  The share is accessible by multiple users, but I'd like each user to connect with her/his own credentials.  My simple solution was just to have users mount the share locally with a mount.cifs command:

sudo mount.cifs //192.168.1.1/Share ~/Share -o user=**someguy**,rw,noperm

     This works for a single local user ("someguy"), but it appears that when multiple local users do the same thing using their own "user=somegal" credentials, permissions get screwy.  For example, when "someguy" had the share mounted first and then "somegal" issues a similar mount command second

sudo mount.cifs //192.168.1.1/Share ~/Share -o user=**somegal**,rw,noperm

it appears that the permissions for the  "someguy" mount update to "somegal".  I have a vague idea that the second mount command is updating/overriding the first, but the details aren't clear.

      I understand that my approach is probably naive, so any help would be greatly appreciated.  Again, I'd prefer to have users connect to the share with their own credentials if possible.  Thanks in advance!

---

### Post by SeijiSensei on 2016-09-15
If someguy and somegal are sharing one client machine, then the second user's mount may well overwrite the first.  I doubt it's possible to do what you want with mount.cifs.

You might try having each user access the share via an smb://server/share URL in the file manager and not use a CIFS mount.  They should each then have a separate individualized connection.

---

### Post by dewarrn1 on 2016-09-15
Yup, connecting from within the file manager works well and will (I hope) address some of the permissions issues.  Many thanks!

---

