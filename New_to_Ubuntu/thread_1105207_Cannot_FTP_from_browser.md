---
title: "Cannot FTP from browser"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by alanhood on 2009-03-24
I have just rented an Ubuntu server at Fasthosts, it has pure-pw.

I have set up FTP ok and users can get on from any client and the command line. However users cannot ftp from a browser. They do not even get as far as the password.

In IE6 i get 'Windows cannot access this folder'

In FireFox I get 'The document contains no data'

Can anybody help?

Many thanks

---

### Post by albandy on 2009-03-24
this is because you don't allow anonymous acces, the browser tries to use anonymous by default.

in url type:

```
ftp://user:password@ftp.myserver.com
```

---

### Post by alanhood on 2009-03-26
Thank you albandy, that worked.

I still have one query.

I have tried to access an ftp server that does not allow anonymous ftp before and got a prompt box up that says something like 'site does not allow anonymous ftp' but then allows me to enter a user name and password. My site does not do this it just gives the errors stated. Is there a way that I can make it give the prompt box?

---

### Post by albandy on 2009-03-26
what ftp server are you using?

---

### Post by alanhood on 2009-03-27
Using Pure-FTPd

---

### Post by albandy on 2009-03-27
I've been reading the documentation and found nothing about this. Could you use other ftpd ?

---

### Post by alanhood on 2009-03-27
Can you recommend one ?

---

### Post by albandy on 2009-03-27
vsftpd (Very Secure ftpd)
after installed edit /etc/vsftpd.conf
set local_enable=YES
and anonymous_enable=NO

---

