---
title: "SSH Keys not working"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by pteri498 on 2010-08-18
I'm trying to get a user to log in successfully with public key authentication. My own user can log in fine this way, but for some reason it's not working out with this new user.

The SSH server does not allow password logins. I'm trying all this from localhost, since if I can't log in from the same computer, there's something deeply wrong.

```

$ cat .ssh/id_rsa.pub > .ssh/authorized_keys
$ ls -l .ssh
total 16
-rw------- 1 angela angela  413 2010-08-18 12:00 authorized_keys
-rw------- 1 angela angela 1675 2010-08-18 11:53 id_rsa
-rw-r--r-- 1 angela angela  413 2010-08-18 11:53 id_rsa.pub
-rw-r--r-- 1 angela angela  442 2010-08-18 11:54 known_hosts

$ ssh angela@localhost -i .ssh/id_rsa
Permission denied (publickey).

```

verbose ssh doesn't tell me much useful information, I feel:

```

$ ssh angela@localhost -i .ssh/id_rsa -v
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file .ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/angela/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: .ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Any ideas?

---

### Post by pteri498 on 2010-08-18
Got it! In my /etc/ssh/sshd_config file, I had AllowUsers set to only my username. I added the other username and I expect this should work now.

---

### Post by bodhi.zazen on 2010-08-18
Change the permissions of the key to 400 (you can not use a key that is readable by "other" ).

---

