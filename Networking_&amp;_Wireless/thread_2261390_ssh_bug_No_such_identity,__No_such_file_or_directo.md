---
title: "ssh bug?: No such identity,  No such file or directory"
date: 2015-01-18
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2015-01-18
Hello

I am trying to ssh to my IPCop firewall but no matter what I do, the connection fails.  I have routinely setup and used ssh to log into my firewall.  This problem occured when I tried to setup a new connection using a new PC loaded with Ubuntu.

It appears I have the bug described in the closed thread:
[http://ubuntuforums.org/showthread.php?t=2145580]("http://ubuntuforums.org/showthread.php?t=2145580")

Any suggested solutions??
Debug output is below:


The IPCop server settings are:
User root
Port 8022
Hostname ipcop.localdomain


```

$ ssh root@ipcop.localdomain -p 8022 -vvv
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ipcop.localdomain [192.168.1.1] port 8022.
debug1: Connection established.

```
IP address and Port are OK.
```

debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/user/.ssh/id_dsa" as a RSA1 public key
debug1: identity file /home/user/.ssh/id_dsa type 2
debug1: identity file /home/user/.ssh/id_dsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/user/.ssh/id_ecdsa" as a RSA1 public key

```
I found threads indicating this error message can be ignored.
```

debug1: identity file /home/user/.ssh/id_ecdsa type 3
debug1: identity file /home/user/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/user/.ssh/id_ed25519 type -1
debug1: identity file /home/user/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.7
debug1: match: OpenSSH_6.7 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [ipcop.localdomain]:8022
debug3: load_hostkeys: loading entries for host "[ipcop.localdomain]:8022" from file "/home/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type ED25519 in file /home/user/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-ed25519-cert-v01@openssh.com,ssh-ed25519
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-ed25519-cert-v01@openssh.com,ssh-ed25519,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ssh-ed25519
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: setup hmac-sha1-etm@openssh.com
debug1: kex: server->client aes128-ctr hmac-sha1-etm@openssh.com none
debug2: mac_setup: setup hmac-sha1-etm@openssh.com
debug1: kex: client->server aes128-ctr hmac-sha1-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ED25519 <place holder for real server host key.
debug3: put_host_port: [192.168.1.1]:8022
debug3: put_host_port: [ipcop.localdomain]:8022
debug3: load_hostkeys: loading entries for host "[ipcop.localdomain]:8022" from file "/home/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type ED25519 in file /home/user/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "[192.168.1.1]:8022" from file "/home/user/.ssh/known_hosts"
debug3: load_hostkeys: found key type ED25519 in file /home/user/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[ipcop.localdomain]:8022' is known and matches the ED25519 host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: ssh_ed25519_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_dsa (0x7f4629441590),
debug2: key: /home/user/.ssh/id_rsa (0x7f4629441630),
debug2: key: /home/user/.ssh/id_ecdsa (0x7f4629442030),
debug2: key: /home/user/.ssh/id_ed25519 ((nil)),

```
So it looks like the keys have been found and read.
```

debug1: Authentications that can continue: publickey,keyboard-interactive
debug3: start over, passed a different list publickey,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering DSA public key: /home/user/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Offering RSA public key: /home/user/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply

```
The public key has been found and sent without any error message.
```

debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Offering ECDSA public key: /home/user/.ssh/id_ecdsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Trying private key: /home/user/.ssh/id_ed25519
debug3: no such identity: /home/user/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply

```
The error messages indicate the keys can't be found.
No password is asked for.
```

debug1: Authentications that can continue: publickey,keyboard-interactive
debug3: userauth_kbdint: disable: no info_req_seen
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).


```
The contents of the .ssh folder looks like this
```

user@odessey:~$ ls .ssh -l
total 32
-rw------- 1 user user  668 Jan 19 09:43 id_dsa
-rw-r--r-- 1 user user 604 Jan 19 09:43 id_dsa.pub
-rw------- 1 user user 227 Jan 19 09:44 id_ecdsa
-rw-r--r-- 1 user user  176 Jan 19 09:44 id_ecdsa.pub
-rw------- 1 root   user 1679 Jan 16 10:47 id_rsa
-rw-r--r-- 1 root   user  396 Jan 16 10:47 id_rsa.pub
-rw-r--r-- 1 root   user  284 Jan 16 15:27 known_hosts

```

The firewall logs show that the connection is closed by the client preauth.

---

