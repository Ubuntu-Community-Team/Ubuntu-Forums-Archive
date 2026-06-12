---
title: "ftp problems!"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by digitalfiz on 2007-12-20
I am using Ubuntu for a local server and a desktop box all in one at work to save space and money and I have a weird problem with it. When ever someone locally tries to connect via ftp its really slow. Connecting takes a minute or more and getting a directory listing takes even longer. I am using a default install of ubuntu 7.10 (gutsy) with the ProFTPD 1.3.0 Server and im using firestarter to make sure the firewall is off. I have the same setup at home and don't have the same problem so I'm not sure if its a networking issue or what. Can someone help?

---

### Post by victorbrca on 2007-12-20
Just ideas....

1- Have you checked you logs (/var/log/proftpd)?
2- How long does it take to logon from the server?

```
ftp 127.0.0.1
```


Vic.

---

