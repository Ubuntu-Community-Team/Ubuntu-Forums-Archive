---
title: "ssh"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by mohanbylapudi on 2014-04-04
Hi In my college some systems are installed with ubuntu 10.04 and they have 22(ssh) port opened. Now my question is: Is it possible to access those systems remotely without knowing thier password.

---

### Post by m_duck on 2014-04-04
You can only access via SSH if you have an account on the server. For logging in without a password you either need SSH keys set up, or that passwordless logins enabled on the server (unlikely).

If you do not have an account on the server, then no, you can't log in without a password. Also, if you do not have permission to access their computers via SSH, then I would not advise it anyway.

---

### Post by TheFu on 2014-04-04
As said before by m_duck - nope. That is kinda the point of ssh.  Access, but only with authentication.  Authentication can be either password or ssh-keys. Keys are 100000000x more secure than passwords and many systems only allow key-based connections to keep the riff-raff out. ;)

---

