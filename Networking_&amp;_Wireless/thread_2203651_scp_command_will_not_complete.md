---
title: "scp command will not complete"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by agross2 on 2014-02-04
I'm trying to transfer a file from a remote Ubuntu server (11.10) to my local Ubuntu desktop (12.04) while on the remote server via ssh.  When I use scp, the process either fails because the connection is refused, or just stops during the weird handshake it does after the connection is established.

Looking online, I figured the refused connection might be because the default port, 22, wasn't open.  I used the command "netstat" to find an open port, 9099.  When I tried scp again, the connection wasn't refused, but it stopped, as though it was waiting for something:

```
zeitgeist:~> scp -v -P 9099 test_file.txt andrew@128.125.36.180:
Executing: program /usr/bin/ssh host 128.125.36.180, user andrew, command scp -v -t -- .
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 128.125.36.180 [128.125.36.180] port 9099.
debug1: Connection established.
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_rsa type -1
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_rsa-cert type -1
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_dsa type -1
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_dsa-cert type -1
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_ecdsa type -1
debug1: identity file /home/zeitgeist-01/grossa/.ssh/id_ecdsa-cert type -1

```

It just stops after that and stays there. I'm wondering if its trying to get my permission or something, but doesn't know how to open a prompt or something.

Thanks

---

