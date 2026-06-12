---
title: "Connecting to a server thru smbclient"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by LebLinux on 2008-11-28
Hello, I`am running Ubuntu on a Virtual PC, and everything is going fine at work, I want to connect using smbclient to our windows 2003 server in a specific shared folder ip: 192.168.1.39.

However I can list and see all the workgroups and computers using : smbclient -L 192.168.1.1 and just hitting enter on the password field.

however I can also connect and see the directories inside the 192.168.1.39 server thru using the Places connect to server or Network. Also I establish this connection by entering the Workgroup name and my network user&pass.

How do I connect using commandline smbclient like I do using Places-Network??

I`am om Gutsy.

---

### Post by LebLinux on 2008-12-01
Hello any ideas regarding this issue?

---

### Post by superprash2003 on 2008-12-01
try this way [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by bab1 on 2008-12-01
to list all shares available use:```
smbtree
```

---

