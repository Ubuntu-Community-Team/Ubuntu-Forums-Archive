---
title: "SSH port needs to change"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by adamjkok on 2010-09-01
The proxy at my school blocks port 22 (and about half of everything accessible from port 80 :x). How do I change the port on my SSH server to something else?

Oh, and I'm looking for help, not a lecture on why I shouldn't try to bypass the filter. There is not a provision in the student handbook against SSH, and our Internet policy is VERY thorough. And I'm just using another port, **not** using a proxy or bruteforce-ing my way into the admin panel.

---

### Post by Mike'sHardLinux on 2010-09-01
If you are using a typical home router, just pick a higher port number like 39034 and tell your router to forward incoming TCP on port 39034 to your server's port 22. Then, you can just ssh to your public ip address on port 39034 (or which ever port you choose).

---

### Post by wojox on 2010-09-01
[OpenSSH Server]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html")

---

### Post by _0R10N on 2010-09-03
You must edit the file
```
/etc/ssh/sshd_config
```
There you will find that one of the top lines specifies the port (22). So, you can change it to whatever you want it to be.

---

