---
title: "Using 'scp' to transfer files to you local machine (ssh)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by tuathan on 2008-04-25
How exactly do i use the 'scp' secure copy command to transfer files to my local desktop (for example)
say i've got <file1> on a remote machine in /C1/users/user1 and i want to transfer it to my local machine desktop...thanks.

---

### Post by Monicker on 2008-04-25
scp username@<ipaddress>:/C1/users/user1/file /local/directory

scp username@192.168.1.1:/C1/users/user1/file /local/directory , for example

---

