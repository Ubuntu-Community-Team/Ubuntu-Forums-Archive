---
title: "OpenSSH doesn't require a password"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by jrtboht on 2011-02-19
I've set up a webserver that I can connect to remotely using OpenSSH.  Everything is working except it seems I don't need a password to gain access (only know the ip address and what port ssh is running on).  How do I secure this?

---

### Post by ajgreeny on 2011-02-19
There is quite a lot of info at [SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")  which should help you.

---

### Post by CharlesA on 2011-02-19
If you only know the ip address and the port, you still won't be able to connect without a valid username.

Unless you are using a passphrase-less key, you will be prompted for a password.

---

