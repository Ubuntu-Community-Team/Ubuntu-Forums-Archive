---
title: "Odd/Unreliable SSH Connections"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by dj_haruko on 2007-05-04
Here's an odd problem I've started having after upgrading to Feisty: I can initiate use SSH once per reboot.  In other words, if I use SSH once, I need to reboot to get it working again, regardless of what machine I'm trying to log into.  When I try to use SCP or sshfs, the same things happen.  Here is the output from SSH using a single -v option:

OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/andrew/.ssh/identity type -1
debug1: identity file /home/andrew/.ssh/id_rsa type -1
debug1: identity file /home/andrew/.ssh/id_dsa type 2
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.4
debug1: match: OpenSSH_4.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xxx.xxx.xxx.xxx' is known and matches the RSA host key.
debug1: Found key in /home/andrew/.ssh/known_hosts:30
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

Also, SSH has been printing some funny characters after I issue the command.  One of them looks like a circle with for pegs/burrs/lines coming out of it, and then the address of the machine I'm connecting to is usually followed by 134.  I'm not sure if this is related.

Any ideas what's going on?

---

### Post by Metacarpal on 2007-05-05
In your home folder, view hidden files (or do an ls -a if you're in terminal) - do you have a .ssh directory?

---

