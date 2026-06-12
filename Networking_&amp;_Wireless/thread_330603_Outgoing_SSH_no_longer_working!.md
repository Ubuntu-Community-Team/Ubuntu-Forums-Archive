---
title: "Outgoing SSH no longer working!"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by NinjitsuStylee on 2007-01-03
It's the strangest thing.  I've been able to ssh from my machine out to other machines every day for the past umpteen days, but last night, something must've changed.

I can't ssh out from my machine anymore!  Here's what happens if I try to ssh into any server (I've tried two of them, both which let me in just fine if I use putty from a windows client here at work).  I've replaced my username/server info with generic stuff but other than that it's a direct paste:



```
$ ssh -v myserver.com
OpenSSH_4.2p1 Debian-7ubuntu3.1, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to myserver.com [208.97.177.175] port 22.
debug1: Connection established.
debug1: identity file /home/myusername/.ssh/identity type -1
debug1: identity file /home/myusername/.ssh/id_rsa type -1
debug1: identity file /home/myusername/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.8.1p1 Debian-8.sarge.6
debug1: match: OpenSSH_3.8.1p1 Debian-8.sarge.6 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myserver.com' is known and matches the RSA host key.
debug1: Found key in /home/myusername/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
```


.....and thats it! No login prompt, nothing!  It just hangs here forever!  The same thing happens if I try to use the -l switch and enter as a user...it sits here and hangs until I Ctrl+C it.

I haven't really changed anything in any settings within the past few days, nor have I messed with my network.  I am behind a NAT firewall (router) but I'm not sure if that makes much of a difference for outbound connections...unless someone is doing something fishy on my network....

Anyways, help would be much appreciated, because I need to get this fixed ASAP so I can get back to work!

](*,)

---

### Post by NinjitsuStylee on 2007-01-03
I've been messing with my network settings, and still no luck......anybody know the culprit? Maybe it has to do with authentication?

---

### Post by NinjitsuStylee on 2007-01-04
Problem solved:  Had to delete a junk file in /tmp/ssh-(random letters here).

Thanks to the good folks in ##linux :) (particularly infi)

---

### Post by napzilla on 2007-06-12
Wow, that was really strange. Prior to your solution, I was reduced to using one of the virtual terminals for all my "SSH-ing". Do you have any idea what triggered the problem in the first place?

---

