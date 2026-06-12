---
title: "[SOLVED] ssh keygen not working"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Nampla on 2008-05-14
i have created a new key after the latest update. i copied over to the remote machine with scp and put it in authorized_keys2 but whenever i log in it still asks for a password. this is a problem at two of the 6 locations i ssh into but the other 4 work perfectly.

dont know what else to do

HELP

---

### Post by prestomation on 2008-05-14
Are they all your machines?  The remote host has to allow public/private keys, the access control may simply not be in place.

---

