---
title: "ssh: hash mismatch"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by ivomans on 2007-05-12
I'm a frequent user of ssh connections to a couple of servers. Yesterday I suddenly can't connect to any other server from my Kubuntu Feisty workstation with ssh any more. All I get is this message:
```
hash mismatch
key_verify failed for server_host_key
```Additional info:[LIST]
[*]When I try to connect to those servers from another workstation there is no problem.
[*]Only a "ssh localhost" is still working
[*]Tried a reinstall of ssh and openssh-client, but without any improvement[/LIST]Hope somebody can suggest a direction to solve this.

---

### Post by awin on 2007-07-10
restarting the pc should work

---

### Post by louman on 2007-07-10
Try this:
```
rm ~/.ssh/known_hosts
```

---

### Post by ivomans on 2007-07-10
Thanks louman and awin for your suggestions. I already tried both but both didn't give a solution.

---

### Post by kevdog on 2007-07-10
Try ssh -v or ssh -v -v or even ssh -v -v -v (Each increases verbosity mode).  With this "debugging mode" maybe it will be easier to get a handle on the problem.

---

### Post by ivomans on 2007-07-10
> **kevdog said:**
> Try ssh -v or ssh -v -v or even ssh -v -v -v (Each increases verbosity mode).  With this "debugging mode" maybe it will be easier to get a handle on the problem.

Here my output. :???:

In this case it's connecting to a server (with Ubuntu Edgy) that is accepting ssh connections from other systems without any problem. I get similar output when I try to connect to other servers, so the problem really seems on my "im12" system (Kubunty Feisty).

```

im@im12:~$ ssh -v -v -v ****.****.**
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ****.****.** [###.###.###.###] port 22.
debug1: Connection established.
debug1: identity file /home/im/.ssh/identity type -1
debug1: identity file /home/im/.ssh/id_rsa type -1
debug1: identity file /home/im/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 530/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host '****.****.**' is known and matches the RSA host key.
debug1: Found key in /home/im/.ssh/known_hosts:1
debug2: bits set: 503/1024
hash mismatch
debug1: ssh_rsa_verify: signature incorrect
key_verify failed for server_host_key

```

---

### Post by kevdog on 2007-07-10
I know this sounds like a stretch, but can you in your ssh settings ~/.ssh/config change HashKnownHosts from yes to no.  Also rm the known_hosts file.

---

### Post by ivomans on 2007-07-10
Since I didn't have a personal .ssh/config I edited /etc/ssh/ssh_config to 'HashKnownHosts no' and also removed the known_hosts file but result was almost same.

```

im@im12:~/.ssh$ ssh -v -v -v ****.****.**
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ****.****.** [##.##.##.##] port 22.
debug1: Connection established.
debug1: identity file /home/im/.ssh/identity type -1
debug1: identity file /home/im/.ssh/id_rsa type -1
debug1: identity file /home/im/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 130/256
debug2: bits set: 525/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host ****.****.**
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /home/im/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host ****.****.**
The authenticity of host '****.****.** (##.##.##.##)' can't be established.
RSA key fingerprint is 11:84:ee:2f:b6:96:bf:12:79:c6:e1:c4:a5:53:42:2d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '****.****.**,##.##.##.##' (RSA) to the list of known hosts.
debug2: bits set: 514/1024
hash mismatch
debug1: ssh_rsa_verify: signature incorrect
key_verify failed for server_host_key

```

---

### Post by kevdog on 2007-07-10
Only last thing I can think of is to reinstall the public key on the server, or generate a new private/public key combination.  You probably dont want to do this, but Im no expert on ssh configuration.  I guess you could just try a new key pair combination with one machine to see if that works.

---

### Post by ivomans on 2007-07-10
Kevdog, thanks for your suggestions. I'm not authorized for changing keys on the server. Shouldn't be necessary because from other systems the server is working fine.

I just did another experiment: I created a brand new user on the im12 system. However this new user got same error using ssh. So it shouldn't be related to some ~/.ssh setting but something from the complete system.

:confused:

---

