---
title: "ssh public/private key fail"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2008-11-06
When I try and set up pub/priv key authentication I am still asked to put in a password.  Here is output of ssh -vvv.  I copied a known working authorized_keys file with the servers public key in it to my desktop.  The server is unable to connect without typing in a password.  Why is this happening?

```
OpenSSH_4.6p1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.12.90 [192.168.12.90] port 22.
debug1: Connection established.
debug1: identity file /u1/dcpa/work/.ssh/identity type -1
debug1: identity file /u1/dcpa/work/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /u1/dcpa/work/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /u1/dcpa/work/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 120/256
debug2: bits set: 510/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /u1/dcpa/work/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.12.90' is known and matches the RSA host key.
debug1: Found key in /u1/dcpa/work/.ssh/known_hosts:1
debug2: bits set: 525/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /u1/dcpa/work/.ssh/identity (0)
debug2: key: /u1/dcpa/work/.ssh/id_rsa (0)
debug2: key: /u1/dcpa/work/.ssh/id_dsa (8089890)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
[B]debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /u1/dcpa/work/.ssh/identity
debug3: no such identity: /u1/dcpa/work/.ssh/identity
debug1: Trying private key: /u1/dcpa/work/.ssh/id_rsa
debug3: no such identity: /u1/dcpa/work/.ssh/id_rsa
debug1: Offering public key: /u1/dcpa/work/.ssh/id_dsa
debug3: send_pubkey_test[/B]
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

```

Regenerating the keys is NOT an option as we are using a setup that already works (with all the other machines except mine :P)

---

### Post by Hawk__0 on 2008-11-07
I finally fixed my problem, posting back to help anyone else to may have this same problem.

I have no idea what caused this, but the fix is simple.

Basically I created a new user, copied my key from my .ssh folder to the new users folder and when I ssh'd from my server it logged in perfectly.

Fixing the problem:
1. Delete your ssh folder:
```
$cd ~
$rm -fr .ssh
```
2. Recreate the folder:
```
$ssh localhost
$exit (close ssh connection to localhost)
```
3. Copy your key back over (In my case, I just copied the key from my other user... which was copied from my server in the first place)
```

user1 .ssh$cd ~/.ssh
user1 .ssh$sudo cp ../../user2/.ssh/authorized_keys .

```
4. Change ownership of the key file (if needed, which mine was because another user owned the one I copied)
```
user1 .ssh$sudo chown user1:user1 authorized_keys
```


Done.  The problem was fixed.  Hopefully this helps someone else out, I spent 3 days troubleshooting this!

---

### Post by subssn594 on 2009-02-05
The root cause for this (I had similar pain diagnosing this) is that your key from the client (where you execute the ssh command) is blacklisted.  See the ssh-vulnkey man page.  You need to generate a new set of keys with a patched ssh, and distribute the new public key to the target (server?) systems.

---

