---
title: "after upgrading to feisty I can nolonger connect to some sites"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by nosbod on 2007-04-30
Hi,

i upgraded to feisty from the previous release through the update manager.
Both my wireless card and my ethernet card work........on some sites.
The problem is that I can't connect to any of my work servers. The connection just hangs.
I've tried ssh, http, ftp. The result is the same. I have tried taking the machine and trying it on a different LAN to the one I am currently on. The result is the same. Most sites i connect to are fine. It is my work servers that I can't connect to. 
Now, if i ssh to another machine on my LAN and from there connect to the work servers i can get a connection. So, it is nothing to do with the LAN setup. It must be feisty. It was fine with Dapper.

Here is what I get when I run ssh -v

OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 138.37.x.x [138.37.x.x] port 22
debug1: Connection established.
debug1: identity file /home/bla/.ssh/identity type -1
debug1: identity file /home/bla/.ssh/id_rsa type -1
debug1: identity file /home/bla/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version 3.2.0 SSH Secure Shell (non-commercial)
debug1: no match: 3.2.0 SSH Secure Shell (non-commercial)
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent

And then it just hangs.
Anybody any ideas?
(I've commented out the GSSAPI lines in the ssh_config.)

Any help appreciated, this has me totally stumped and preventing me working from home!!

cheers

---

