---
title: "VSFTPD ftp server"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-12-24
I have configured vsftpd and my configuration details are given below.However when i type [ftp://127.0.0.1](ftp://127.0.0.1) in my browser it takes me to my home directory instead of /srv/ftp..Why?

```
listen=YES
anonymous_enable=YES
anon_root=/srv/ftp
local_enable=YES
write_enable=YES
use_localtime=YES
xferlog_enable=YES
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

---

### Post by HermanAB on 2010-12-24
My guess is the local enable.

You should go to the vsftpd project web site and read the manual.  It is quite involved.

---

### Post by karthick87 on 2010-12-24
It's not the problem...local_enable is used for logging in locally..

---

### Post by pricetech on 2010-12-24
Because you're not logging in anonymously ????

---

### Post by karthick87 on 2010-12-24
No i am logging in anonymously..

---

### Post by karthick87 on 2010-12-24
Solved it thanks for all who helped me..It's a file permission  problem..

---

