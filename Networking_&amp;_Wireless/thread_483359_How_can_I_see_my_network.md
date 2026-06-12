---
title: "How can I see my network?"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by Ifaistos on 2007-06-24
Hello :)

My Home network setup is as follows.

Comp 1 : 4HD. 1 is Linux, 2,3 and 4 are NTFS former WInXP.
Comp 2 : 4 HD. 1,2 is Linux and 2,3 are NTFS dual boot with winXP.
Comp3 : 3 HD, all of them NTFS and system currently running WinXP.
Laptop with 3HD.  all of them NTFS and system currently running WinXP.

My Comp 1 can see all NTFS partitions through Samba but cannot see the Linux HDs on comp 2.
Windows can see only NTFS partitions and only if they are shared by windows.

How can I make everyone see everything.  More specifically how can I make comp 1 see all NTFS and Linux partitions on the Network?

Can someone direct me to a guide?

Thank you :-)

---

### Post by scrooge_74 on 2007-06-24
You can either setup SAMBA servers on all Linux systems so all XP machines can see them or you can NFS those drives on Linux systems for other Linux systems to see them

---

### Post by Ifaistos on 2007-06-25
Thank you Scrooge :-)

The only problem is that I am a noob and I don't know how to do that...  Is there a guide that you can direct me to?

Does anyone know any other solution(s)?

Please direct me to a guide on how to implement your solution.
Be specific :-)

Thank you all in advance :)

---

### Post by scrooge_74 on 2007-06-25
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html)

This should point you in the correct direction

---

