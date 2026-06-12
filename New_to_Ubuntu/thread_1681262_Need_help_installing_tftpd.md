---
title: "Need help installing tftpd"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by samohung390 on 2011-02-03
hello, any can help me setting up tftpd? im having trouble with it.
-the first ubuntu pc, i installed it first with filezilla then installed tftpd using "apt-get", transfer of file to the server keeps failing.

-then second reinstall, without filezilla ftp, it transfers successfully.

-third time, new install with filezilla again, file transfer again doesnt work.

I used this instructions for tftp: 
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

is the filezilla the problem? anyone also having problems like this? thanks

---

### Post by sandyd on 2011-02-03
> **samohung390 said:**
> hello, any can help me setting up tftpd? im having trouble with it.
-the first ubuntu pc, i installed it first with filezilla then installed tftpd using "apt-get", transfer of file to the server keeps failing.

-then second reinstall, without filezilla ftp, it transfers successfully.

-third time, new install with filezilla again, file transfer again doesnt work.

I used this instructions for tftp: 
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

is the filezilla the problem? anyone also having problems like this? thanks
Did you set port to ->
```
69
```
in filezillla?

---

### Post by samohung390 on 2011-02-03
the filezilla is set to its default port, didnt change it, i think its on port 21

---

### Post by samohung390 on 2011-02-03
also i restarted already xinetd, still doesnt work

---

### Post by sandyd on 2011-02-03
I don't think tftpd + filezilla work.

try pure-ftpd instead (after removing tftpd).
pureftpd works straight out of the box.

---

### Post by samohung390 on 2011-02-04
is it also installed using apt-get?

---

### Post by samohung390 on 2011-02-04
but i really need to use tftpd

---

### Post by sandyd on 2011-02-04
> **samohung390 said:**
> but i really need to use tftpd
then use the tftpd client with a tftpd server.

TFTPD stands for Trivial File Transfer Protocol, not the normal ftp.

---

