---
title: "ssh connection refused"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by gilbert_liou on 2014-07-23
I'm using Ubuntu 14.04  LTS.
I just re-install openssh-client, openssh-server, and want to connect it from remote client.
NowI'm testing it on my local server.

if I try to connect like this:

>> ssh gilbert@localhost --> it works.
>> ssh gilbert@192.168.1.103 --> it also works.

But if I try to connect it from my real ip, I met some problem:

>> ssh -v gilbert@61.228.24.172 -p 12091
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 61.228.24.172 [61.228.24.172] port 12091.
debug1: connect to address 61.228.24.172 port 12091: Connection refused
ssh: connect to host 61.228.24.172 port 12091: Connection refused

I have tried to change iptables ([http://superuser.com/questions/368333/ssh-connection-refused):](http://superuser.com/questions/368333/ssh-connection-refused):)

>> iptables -A INPUT -i ethX -p tcp --dport 12091 -m state --state NEW,ESTABLISHED -j ACCEPT 
>> iptables -A OUTPUT -o ethX -p tcp --sport 12091 -m state --state ESTABLISHED -j ACCEPT

and my router allows any internet access.
I tried to solve this problem for two days but still failed.
Does anyone know how to solve this problem?

Thanks.

---

### Post by sedawk on 2014-07-23
Why port 12091. Have yoo configured your firewall/router to forward port 12091 to ssh-port on 192.168.1.103?
You might have to check your firewall/router setup and not your Ubuntu ...

---

### Post by gilbert_liou on 2014-07-24
I've changed my port to default 22.
But meet another problem:

>>> ssh -vvvvv  61.228.24.172
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug2: ssh_connect: needpriv 0
debug1: Connecting to 61.228.24.172 [61.228.24.172] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/gilbert/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/gilbert/.ssh/id_rsa type 1
debug1: identity file /home/gilbert/.ssh/id_rsa-cert type -1
debug1: identity file /home/gilbert/.ssh/id_dsa type -1
debug1: identity file /home/gilbert/.ssh/id_dsa-cert type -1
debug1: identity file /home/gilbert/.ssh/id_ecdsa type -1
debug1: identity file /home/gilbert/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/gilbert/.ssh/id_ed25519 type -1
debug1: identity file /home/gilbert/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version dropbear_0.46
debug1: no match: dropbear_0.46
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "61.228.24.172" from file "/home/gilbert/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: setup hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: setup hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: bits set: 523/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
Read from socket failed: Connection reset by peer


--
I tried to telnet to my real ip and it works.
so I think maybe it's not the router problem.
Am I right?

---

