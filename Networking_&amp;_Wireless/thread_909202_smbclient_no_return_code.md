---
title: "smbclient no return code?"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by pfastre on 2008-09-03
Hello

I've finally switched from Slackware to Ubuntu for my servers.
Unfortunately, I've a problem with smbclient, which doesn't return any error code if something goes wrong, making my scripts having a hard time.

smbclient //ip/Homes -D "/leraar/badfolder" -U hayru%pass -c "ls"
Domain=[TEST] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]
cd \leraar\badfolder\: NT_STATUS_OBJECT_NAME_NOT_FOUND
root@mail01:/var/www/schoolwise# echo $?
0

Shouldn't this return an error code? It did on my old slackware servers, which are using a self-compiled Samba.

What can we do?

Peter

---

