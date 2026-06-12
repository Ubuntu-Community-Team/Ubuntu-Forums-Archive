---
title: "SSH Failure"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by shoaibi on 2009-09-10
I have Jaunty, have modified a bit of ssh configs, i had 10 keys pairs for different servers, so created my config, then renamed it to old.config as many servers were giving strange errors like in the one below where it doesnt even ask me for the password. This server is a fresh ubuntu-server install with root ssh allowed, no fw, denyhosts, or fail2ban.

```

ssh root@hilux -vvvv                                                                                                        (10/09/09 10:55:17)
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to hilux [192.168.40.143] port 22.
debug1: Connection established.
debug1: identity file /home/shoaibi/.ssh/identity type -1
debug3: Not a RSA1 key file /home/shoaibi/.ssh/id_rsa.
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
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/shoaibi/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/shoaibi/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 134/256
debug2: bits set: 528/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/shoaibi/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 23
debug3: check_host_in_hostfile: filename /home/shoaibi/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 24
debug1: Host 'hilux' is known and matches the RSA host key.
debug1: Found key in /home/shoaibi/.ssh/known_hosts:23
debug2: bits set: 531/1024
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
debug2: key: /home/shoaibi/.ssh/id_rsa (0x7f37ce5f5a40)
debug2: key: shoaibi@blade (0x7f37ce5fc550)
debug2: key: shoaibi@blade (0x7f37ce5fe2d0)
debug2: key: shoaibi@revolution-next.lan (0x7f37ce5fe4f0)
debug2: key: shoaibi@blade (0x7f37ce5fe5e0)
debug2: key: shoaibi@blade (0x7f37ce5fe620)
debug2: key: /home/shoaibi/.ssh/identity ((nil))
debug2: key: /home/shoaibi/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/shoaibi/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: shoaibi@blade
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: shoaibi@blade
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: shoaibi@revolution-next.lan
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: shoaibi@blade
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: shoaibi@blade
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
Received disconnect from 192.168.40.143: 2: Too many authentication failures for root

```

[EDIT]:

```

[615][shoaibi@blade:~]$ ls ~/.ssh/*                                                                                                                 (10/09/09 11:10:36)
/home/shoaibi/.ssh/soho       /home/shoaibi/.ssh/id_rsa.pub              /home/shoaibi/.ssh/misc            /home/shoaibi/.ssh/office
/home/shoaibi/.ssh/soho.pub   /home/shoaibi/.ssh/id_rsa.pub.other  /home/shoaibi/.ssh/misc.pub        /home/shoaibi/.ssh/office.pub
/home/shoaibi/.ssh/id_rsa           /home/shoaibi/.ssh/shellhell                   /home/shoaibi/.ssh/new_id_rsa
/home/shoaibi/.ssh/id_rsa.keystore  /home/shoaibi/.ssh/shellhell.pub               /home/shoaibi/.ssh/new_id_rsa.pub
/home/shoaibi/.ssh/id_rsa.old       /home/shoaibi/.ssh/known_hosts             /home/shoaibi/.ssh/old.config
[616][shoaibi@blade:~]$ file ~/.ssh/*                                                                                                               (10/09/09 11:13:30)
/home/shoaibi/.ssh/soho:             ASCII text
/home/shoaibi/.ssh/soho.pub:         ASCII text, with very long lines
/home/shoaibi/.ssh/id_rsa:                 ASCII text
/home/shoaibi/.ssh/id_rsa.keystore:        ASCII text, with very long lines
/home/shoaibi/.ssh/id_rsa.old:             ASCII text, with very long lines
/home/shoaibi/.ssh/id_rsa.pub:             ASCII text, with very long lines
/home/shoaibi/.ssh/id_rsa.pub.other: ASCII text, with very long lines
/home/shoaibi/.ssh/shellhell:                  ASCII text
/home/shoaibi/.ssh/shellhell.pub:              ASCII text, with very long lines
/home/shoaibi/.ssh/known_hosts:            ASCII text, with very long lines
/home/shoaibi/.ssh/misc:                   ASCII text
/home/shoaibi/.ssh/misc.pub:               ASCII text, with very long lines
/home/shoaibi/.ssh/new_id_rsa:             ASCII text
/home/shoaibi/.ssh/new_id_rsa.pub:         ASCII text, with very long lines
/home/shoaibi/.ssh/old.config:             ASCII text
/home/shoaibi/.ssh/office:              ASCII text
/home/shoaibi/.ssh/office.pub:          ASCII text, with very long lines

```

[/EDIT]

Anyone has ideas?
it should atleast ask me for password for the very least, right?

---

### Post by neurostu on 2009-09-10
well that really depends on what kind of change you made to the config file, also this is a bit more complicated than beginner talk, you might consider posting to a more advanced forum.

---

