---
title: "Problems with slow establishment of ssh connections"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by tdn on 2007-09-28
Hi

I am experiencing problems with connecting to a host on the LAN via SSH.
The client runs Ubuntu with OpenSSH version:
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006

The server runs Debian Etch with OpenSSH version:
OpenSSH_4.3p2 Debian-9, OpenSSL 0.9.8c 05 Sep 2006

When I open an ssh connection to the server (10.0.0.30) it just
"hangs" for several seconds before it logs in.

I have tried using ssh -vvv for extra verbosity, but I do not
understand what's wrong.

When it comes to:
debug1: identity file /home/tdn/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version
OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK

It just hangs here.

Then after several seconds it writes:

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

Then hangs again several seconds.
Then it writes:

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received

After this, the connection is established pretty quickly.


Is this a DNS problem?
If so, what do I need to do to fix it?

The full output from ssh -vvv is available at:
[http://thomasdamgaard.dk/paste/P962.html](http://thomasdamgaard.dk/paste/P962.html)
I have inserted "[waiting...]" between the lines where it hangs.

---

### Post by tdn on 2007-09-28
Hi

I posted this on Debian Forums too, since the server is Debian. Other thread here:
[http://forums.debian.net/viewtopic.php?p=103248](http://forums.debian.net/viewtopic.php?p=103248)

---

