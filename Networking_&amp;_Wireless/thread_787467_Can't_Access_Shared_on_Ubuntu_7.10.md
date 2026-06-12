---
title: "Can't Access Shared on Ubuntu 7.10"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by erbag on 2008-05-08
I can't access files on my Ubuntu box from my window box or mac. What did I do wrong?

---

### Post by superprash2003 on 2008-05-09
firstly ensure that the two computers are able to ping each other.. then follow the samba guide here [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by erbag on 2008-05-09
I tried following the guide and was unable to add or edit users. Should I remove samba and then try installing it using the guide provided?

---

### Post by superprash2003 on 2008-05-09
i dont think that is required.. remember you can only add users that are present in system->administration->users and groups .. suppose you are trying to add user1 in samba.. then first create user1 under system->administration->users and groups  and then add it in samba

---

### Post by erbag on 2008-05-18
so my box crashed and I re-installed all Ubuntu 7.10 - I can now connect from my windows box but not from my iMac. I keep getting an  error to that my alias is broken.

---

### Post by erbag on 2008-05-20
I found the solution. On the Samba Server I had **password encrypt = no** when it should have been **yes**.

---

### Post by mapes12 on 2008-05-20
I am also running 7.10

I couldn't get sharing to work at all across my home LAN therefore I gave up on network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

