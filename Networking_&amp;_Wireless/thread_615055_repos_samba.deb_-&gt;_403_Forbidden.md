---
title: "repos: samba.deb -&gt; 403 Forbidden?"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by foerdi on 2007-11-16
Why is the file [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
forbidden?

---

### Post by scorp123 on 2007-11-16
Good question. I ran into the same error tonight. Looks to me as if the file permissions are wrong so us folks from outside can't access the file. I guess one of the admins will correct this soon.

---

### Post by TLM on 2007-11-16
looks like 3 files in that directory. libsmbclient, smbclient and samba-bommon

---

### Post by arist0tle on 2007-11-16
Yeah I have the same problem. Probably permissions issue on the server side. Everyone makes mistakes :-)

---

### Post by Nem1976 on 2007-11-16
Thats wierd I did that updates this morning and it went through just fine.  But my coworker just tried to update and is getting the same message.

---

### Post by taurus on 2007-11-16
This happened this afternoon.

[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

---

### Post by veloce on 2007-11-16
> **taurus said:**
> This happened this afternoon.

[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)

and the relevance of this link is??????  I know I'm a bit of a noob, but I don't understand.  Is this a reason that those files are forbidden or what?

---

### Post by taurus on 2007-11-16
> **veloce said:**
> and the relevance of this link is??????  I know I'm a bit of a noob, but I don't understand.  Is this a reason that those files are forbidden or what?

[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by foerdi on 2007-11-16
took it from here [http://de.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)

works

---

### Post by rustybronco on 2007-11-16
change your software sources to main and then do the updates.

---

