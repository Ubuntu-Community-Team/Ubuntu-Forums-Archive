---
title: "can I setup sftp with proftpd?"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by billdotson on 2007-05-08
I want an encrypted FTP connection for my server and I have recently heard about sftp.  Can I do sftp with proftpd and gproftpd?  I have heard about tunneling connections through ssh but I was wodering if this keeps both the passwords and the data encrypted.

thanks

---

### Post by rufius on 2007-05-08
sftp is packaged as part of ssh. All it requires is a running ssh server on the box you want to FTP into. Its very simple, just switch 'ssh' with 'sftp' in the command to connect, as follows:

```
ssh bill@dotson.com
```

becomes

```
sftp bill@dotson.com
```

---

### Post by billdotson on 2007-05-08
well how do I set that up with users and permissions and such?  I need a ftp server so that dad can  transfer work stuff.

---

