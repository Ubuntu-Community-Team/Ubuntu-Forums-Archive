---
title: "samba, network domain and login"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by Bouteille on 2008-10-28
Hi all !

I'm setting up a server that will be used simultaneously by several users.

My problem concern the mounting of a network access in one of the the /media folders previously created.

This network is based on a windows domain. So every user has to login in order to be able to browse the network folders. Unfortunately, we don't want to register this server on the domain since we will have specific accounts on it.

What we would like to have at the end is an icon on the desktop for accessing the network. When the user clicks on this icon, we would like a popup that will ask for domain login and password and then allow the user to browse the network.

What I planned to do is to put a mounting command in the fstab using either smbfs or cifs but I don't know how to manage this login and password issue.

Wouls you have any suggestion for me ?

Thank you very much.

Best regards,

Romain.

---

