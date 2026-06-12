---
title: "Samba shares accessible from Windows 10 machine but not Windows 7 ?"
date: 2016-10-19
forum: Networking &amp; Wireless
---

### Post by khkccmbd on 2016-10-19
Hi,

I set up Samba shares on a machine running Ubuntu.

Created a folder /samba/group1 which is owned by group1. Set everything up in the conf file, created users and added them to group1.

All is good, individual logins from Windows 10 work fine, but from Windows 7, users only get read access (no write access).

I can't figure out what to do here, anyone have ideas where this could be coming from ?

Thanks,
Kevin

---

### Post by khkccmbd on 2016-10-19
Solved it, turns out it was a setting with the create/directory masks preventing other users from modifying or creating files inside the common folder...

---

### Post by khkccmbd on 2016-10-19
Solved it, turns out it was a setting with the create/directory masks preventing other users from modifying or creating files inside the common folder...

---

