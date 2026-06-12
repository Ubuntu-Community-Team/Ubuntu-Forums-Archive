---
title: "Can't get samba back"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by core on 2006-12-02
Hi

I've deleted my messed smb.conf hoping to get the default file back after apt-get removing and installing. But a reinstallation somehow doesn't recover the config file, and 'samba start' obviously fails.

How do I get the config back?

Thanks.

---

### Post by Mr Green on 2006-12-14
I'm sort of in the same situation:

Deleted the contents of /etc/samba before apt-get removing and apt-get installing to replace smb.conf and now I'm fookked!

Can anyone post a default smb.conf file here or something so that we can get Samba to run again?

---

### Post by Iowan on 2006-12-14
This one looks pretty stock - or you could search for one of the other **smb.conf** posted on the forums.
[http://www.linuxquestions.org/questions/showthread.php?t=458914]("http://www.linuxquestions.org/questions/showthread.php?t=458914")

---

### Post by Mr Green on 2006-12-18
Recreating smb.conf with the link above worked just fine. Samba is up and running again.

---

