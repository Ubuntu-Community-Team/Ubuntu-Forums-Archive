---
title: "ssh/mysql problems"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by sveri on 2008-11-12
I dont know if this is the right forum, but i hope so.
In my lan i have a mysql/file/mercurial/whatever server
which runs ubuntu server.
Some days ago i upgrade hardy to intrepid and
scince that connecting to that ubuntu server via
mysql or ssh is horrible slow. At least to slow to develop with
it.

I tried ssh -v user@server and it stucks at:
OpenSSH_5.1p1, OpenSSL 0.9.8i 15 Sep 2008
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to odie [192.168.0.133] port 22.
debug1: Connection established.
debug1: identity file /home/sveri/.ssh/identity type -1
debug1: identity file /home/sveri/.ssh/id_rsa type -1
debug1: identity file /home/sveri/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'odie' is known and matches the RSA host key.
debug1: Found key in /home/sveri/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received

that point here.
Than it waits around 5 secs and goes on
to connect normal:

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/sveri/.ssh/identity
debug1: Trying private key: /home/sveri/.ssh/id_rsa
debug1: Offering public key: /home/sveri/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.

When i access mysql via phpmyadmin it is as fast
as normal, but when i try to access it via django
it stucks like ssh.

Any Ideas?


Greetings 
Sven

---

