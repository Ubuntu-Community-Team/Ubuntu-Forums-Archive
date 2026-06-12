---
title: "Hardware change on server, now I can't SSH in"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by jcr1 on 2008-07-11
Hiya,

As the title says, I added a second hard drive to my server...rebooted it, and now I cannot ssh in any more

```

jonr@jonr-laptop:~/.ssh$ ssh -vv jonrserv@192.168.0.4 -p 443
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.4 [192.168.0.4] port 443.
debug1: Connection established.
debug1: identity file /home/jonr/.ssh/identity type -1
debug1: identity file /home/jonr/.ssh/id_rsa type -1
debug1: identity file /home/jonr/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
jonr@jonr-laptop:~/.ssh$ 

```

I can vnc remote control the server but not ssh.

Any ideas?

(the hdd came from an old server, which now also cannot be ssh'd into?)

---

### Post by jcr1 on 2008-07-11
seemingly sorted now...

It seems the ip of the laptop i was trying to connect from had ended up in the deny.hosts

This may be down to denyhosts (the program) i installed (and no removed)

---

