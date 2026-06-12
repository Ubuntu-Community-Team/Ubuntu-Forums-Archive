---
title: "file permissions on nfs shares"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by bigpook on 2008-05-02
machine 'A' is ubuntu server 7.10 acting as a nfs server. I share out a folder called /pub/MONEY.The one file in this directory is flagged as 770 for file permissions. The owner is root and the group is staff.

I have 2 ubuntu clients running 8.04. Client '001' launches the application and opens the file on the 7.10 machine, makes some changes and closes the file.

When I look at the /pub/MONEY folder on the 7.10 machine the file permissions and owner/group are changed. They become 644 and the owner/group is the user on 8.04 that last used the file.

How do I fix this so that both clients can read/write the file that resides on the 7.10 server?

---

