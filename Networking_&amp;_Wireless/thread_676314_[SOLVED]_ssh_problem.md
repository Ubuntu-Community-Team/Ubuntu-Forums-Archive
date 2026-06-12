---
title: "[SOLVED] ssh problem"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by AjitJor on 2008-01-23
Hello

I have a problem with ssh on my Ubuntu 7.04 running on X86_64.
if I do:
**ssh -vvv -l amitm host.somewhere.over.the.ocean**

I get:
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to host.somewhere.over.the.ocean [ip] port 22.
debug1: Connection established.
debug1: identity file /home/amitm/.ssh/identity type -1
debug1: identity file /home/amitm/.ssh/id_rsa type -1
debug1: identity file /home/amitm/.ssh/id_dsa type -1

...  but then it freezes ...

The host runs Fedora7 if that matters.
The odd thing happens if I connect my old machine (i386) that runs Fedora8 and do the same thing and I get a good solid ssh connection. I also tried to change the /etc/ssh/ssh_config file to be similar to that of the FC8 but that did not change a thing.

Help would be most welcomed !

---

