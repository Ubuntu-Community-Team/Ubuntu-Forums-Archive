---
title: "seting two passwords for ssh with PAM"
date: 2018-11-19
forum: Networking &amp; Wireless
---

### Post by hosam.amleh on 2018-11-19
When using putty to "ssh root@address", I'm trying to have the remote  server prompt the user for 2 passwords. The first password is the ssh login password. while the second password  is a different password than the first. I know that I have to modify /etc/pam.d/sshd but after all attempts, ssh  connection is refused  entering the first password. the message is  "access denied unfortunately most resources online discusses PAM with google  authenticator. I'll appreciate your help.

---

### Post by TheFu on 2018-11-19
In a standard Ubuntu installation, the root account is disabled.

---

