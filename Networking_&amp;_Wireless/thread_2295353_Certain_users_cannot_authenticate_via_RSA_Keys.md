---
title: "Certain users cannot authenticate via RSA Keys"
date: 2015-09-17
forum: Networking &amp; Wireless
---

### Post by rcmart on 2015-09-17
Hello I have been struggling with this issue for some time now and cant seem to rectify the problem. When connecting to my linux box (Ubuntu 14.04) via ssh my admin account is able to authenticate fine using 2048 bit private key, however when I try to connect with another user the connection is rejected, some digging in the log turned this up which I am yet to make sense of.

Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug1: restore_uid: 0/0
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: Failed publickey for common from 67.241.178.217 port 54919 ssh2: RSA a3:0c:c8:7a:82:c1:57:84:8f:cd:9e:01:61:8d:46:da
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug3: mm_answer_keyallowed: key 0x7f5916193be0 is not allowed
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug3: mm_request_send entering: type 23
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa [preauth]
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug3: userauth_finish: failure partial=0 next methods="publickey" [preauth]
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: error: Received disconnect from 67.241.178.217: 14: No supported authentication methods available [preauth]
Sep 17 21:03:34 Ubuntu.01 sshd[1353]: debug1: do_cleanup [preauth]

the file permissions for authorized_keys as as follows
-rw------- 1 common root 396 Sep 17 21:01

---

### Post by tgalati4 on 2015-09-17
Welcome to the forums.  I use *seahorse* to manage my ssh keys on servers that I remotely maintain.  When checking the properties, I notice that my key strength is listed as 2064--I presume this means 2064 bits (or perhaps 2048 bits with a checksum?).  What version of ssh are you running on each machine?

```
ssh -V
```

On 14.04 I'm running:

> tgalati4@Mint17 ~/Desktop $ ssh -V
OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3, OpenSSL 1.0.1f 6 Jan 2014


---

### Post by rcmart on 2015-09-29
Thank you for your response, shortly after posting I discovered the problem, the permissions for the parent directory of the user had been set to 777, I rectified the problem by setting the permissions of the parent directory to the user's home folder to 700.

---

### Post by Habitual on 2015-09-29
/home/<user> should be 755 ?
but things change and I'm old(er).

---

