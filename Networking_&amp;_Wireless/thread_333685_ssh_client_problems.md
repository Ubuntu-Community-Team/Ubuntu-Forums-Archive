---
title: "ssh client problems"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by darrdevyl on 2007-01-07
Hello there.  I am a moderately-experienced Linux user, though I still have a great deal more to learn with regards to system administration.  I've used Mandrake/iva for years and have just installed (k)Ubuntu.  So far I really like it.

I cannot SSH from this machine however.  When I try to SSH to a machine at work I get this:

```
root@mymachine:~# ssh -vvv some.server.net
OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to some.server.net [204.244.192.51] port 22.
debug1: connect to address 204.244.192.51 port 22: Connection refused
ssh: connect to host some.server.net port 22: Connection refused
```

Now to get the obvious possible solutions out of the way:

- My internet connection works fine, I can browse the web and the like in Linux.  I can ping the server.
- The server is running the SSH server and does allow access from my machine.  This is a dual-boot with Windows and I can SSH from Windows (with Putty) to the server with no problems.

I asked the sysadmin at work.  He is normally very knowledgeable and helpful but this left him scratching his head.  All he could offer war "check your ipchains".  Well, OK, I can try.

```
root@mymachine:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I'm not familiar with this but OUTPUT/ACCEPT looks like it should allow outgoing connections, right?

Is there anything else I can check?  This is a regular installation of Ubuntu, I haven't done anything funny after installation, so surely someone else would have had this problem?  I hope?

Any help is appreciated.  Thank you in advance!

---

