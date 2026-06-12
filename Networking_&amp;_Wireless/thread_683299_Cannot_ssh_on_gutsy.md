---
title: "Cannot ssh on gutsy"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by dgermann on 2008-01-30
Hi--

I have two Gutsy boxes on my network that cannot connect to one another, nor can other computers connect to them using ssh.

However, I can connect to other computers on the network (Ubuntu 6.06LTS and RedHat 9.0) from these two boxes.

When I run ssh -vvv doug@192.168.0.83, I get:
```
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.83 [192.168.0.83] port 22.
```
and the computer just sits there, does not time out after even a couple of minutes.

The /etc/ssh/sshd_config files are what came out of the box. I have checked on this forum and in Google and have not found anything that seems to deal with this problem.

Same result whether firestarter is running or not.

Any ideas?

Thanks!

---

