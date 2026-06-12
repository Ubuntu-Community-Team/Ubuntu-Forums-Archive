---
title: "'Permission denied (publickey,password)' on ssh attempt"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by Shane_Wignall on 2015-01-11
I have two computers running ubuntu, both have openssh installed. I want to use computer A (192.168.1.5) as a server, and then connect to it with computer B(shane@ubuntu). I have tried countless times, purging the config files and keys and starting over again, but I keep getting this error. I've been looking through forums forever it seems, and I haven't had any luck.. I'm pretty new to this stuff. Help me out? Thanks!

```
shane@ubuntu:~$ sudo ssh -v 192.168.1.5OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.5 [192.168.1.5] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-8
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-8
debug1: match: OpenSSH_6.6.1p1 Ubuntu-8 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 5c:62:49:11:6c:cd:46:eb:ec:33:88:1e:7e:e9:7b:a8
debug1: Host '192.168.1.5' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey,password).
shane@ubuntu:~$ 



```

---

