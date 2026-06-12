---
title: "Connect Remote ubuntu"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by jagadeeshkode on 2008-07-06
I am new ubuntu user, I want to connect various systems through internet and copy files server to clients (ubuntu to ubuntu). I have public IP server. From public IP to private IP I want to copy files. Plz advice and help me.

Thanks in advance.
Jagadish

---

### Post by jpkotta on 2008-07-07
ssh is easy to set up and secure.  The client is installed by default.  On the server:
```
sudo aptitude install openssh-server
```

Then you can use scp to transfer files.
```
scp file user@remote:/path/
```
or
```
scp user@remote:/path/file /local/path/
```

There's also sftp, sshfs, and more.

---

