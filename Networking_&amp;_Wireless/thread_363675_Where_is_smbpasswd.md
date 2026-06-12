---
title: "Where is smbpasswd?"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by boon utnubu on 2007-02-17
Hi everyone,

This is my first post on these forums.

Just a quickie.  I have Samba running sweet as a nut.  I have one quick question for you guys though: Where is the smbpasswd file?  Coming from a Redhat/Suse background (I'm new to Ubuntu) that file is normally kept in /etc/samba/  On My Etchy installation I can't find an smbpasswd file anywhere.

It's all working a treat (smbpasswd -a *username*) but I'd just like to know where the smpasswd is kept.

Not urgent but any response is much appreciated

Cheers guys

:)

---

### Post by chggr on 2007-02-18
Well, if you don't know where a file is, you should search for it. Open a terminal and issue the following command:

sudo find / -name "smbpasswd"

or 

sudo updatedb
locate smbpasswd

---

### Post by bigken on 2007-02-18
/usr/bin/smbpasswd

---

### Post by Lundin on 2007-02-25
As of samba 3, the smbpasswd for password storage does not exist any more (the command is still there). You can read more about it in: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

As I understand it are the passwords stored in passdb.tdb nowadays. On my edgy install is it located /var/lib/samba/

---

### Post by boon utnubu on 2007-02-28
Cheers guys.

---

