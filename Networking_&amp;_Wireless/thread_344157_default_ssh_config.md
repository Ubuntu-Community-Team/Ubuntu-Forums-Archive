---
title: "default ssh config"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by avg.joe on 2007-01-22
I just installed ssh and was just wondering if the default ssh config is secure. Anyone have any tips to make it even more secure? Thanks.

---

### Post by evilghost on 2007-01-22
In /etc/ssh/sshd_config:

Port [Something other than TCP 22]
PermitRootLogin no
MaxAuthTries 1
PasswordAuthentication no

Do not disable PasswordAuthentication until you have configured public key authentication:
[http://www.edafe.org/ubuntu/index.html#authentication](http://www.edafe.org/ubuntu/index.html#authentication)

---

