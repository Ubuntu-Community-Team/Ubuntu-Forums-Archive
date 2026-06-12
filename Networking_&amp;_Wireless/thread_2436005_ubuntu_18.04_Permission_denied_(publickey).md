---
title: "ubuntu 18.04 Permission denied (publickey)"
date: 2020-01-29
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2020-01-29
How do I fix this? I want to be able to go from both boxes to each other.

Can ssh from type40tardis (192.168.2.9) into tardis (192.168.2.5). 

But I can **NOT** go the other way from tardis (192.168.2.5) into type40tardis (192.168.2.9)
ssh -vvv type40tardis
```

$ ssh -vvv type40tardis
OpenSSH_8.0p1 Ubuntu-6build1, OpenSSL 1.1.1c  28 May 2019
debug1: Reading configuration data /home/lance/.ssh/config
debug1: /home/lance/.ssh/config line 1: Applying options for *
debug1: /home/lance/.ssh/config line 19: Applying options for type40tardis
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.2.9 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.168.2.9 [192.168.2.9] port 22.
debug1: Connection established.
debug1: identity file /home/lance/.ssh/id_rsa type 0
debug1: identity file /home/lance/.ssh/id_rsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.0p1 Ubuntu-6build1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.4*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.2.9:22 as 'lance'
debug3: hostkeys_foreach: reading file "/home/lance/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/lance/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 192.168.2.9
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: zlib@openssh.com,zlib,none
debug2: compression stoc: zlib@openssh.com,zlib,none
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: zlib@openssh.com
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: zlib@openssh.com
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:zfZkRRE0MZ2+Haz9voe5pahSrGjIDK67KeKZ5Wnapnk
debug3: hostkeys_foreach: reading file "/home/lance/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/lance/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 192.168.2.9
debug1: Host '192.168.2.9' is known and matches the ECDSA host key.
debug1: Found key in /home/lance/.ssh/known_hosts:1
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey out after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey in after 134217728 blocks
debug1: Will attempt key: /home/lance/.ssh/id_rsa RSA SHA256:Y+jwHyu/00K4C2BxCA1bBbed4H1lEvqNOktE59+evZk explicit agent
debug2: pubkey_prepare: done
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/lance/.ssh/id_rsa RSA SHA256:Y+jwHyu/00K4C2BxCA1bBbed4H1lEvqNOktE59+evZk explicit agent
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
lance@192.168.2.9: Permission denied (publickey).

```

 ~/.ssh folder on both linux boxes
```

drwx------  2 lance lance      4096 Mar  3 10:12 .ssh #700
-rw------- 1 lance lance 3326 Dec  8 19:22 id_rsa # 600
-rw-r--r-- 1 lance lance 1880 Dec  8 19:31 authorized_keys #644
-rw-r--r-- 1 lance lance  744 Dec  8 19:22 id_rsa.pub
-rw-r--r-- 1 lance lance  666 Dec  8 19:41 known_hosts
-rw-r-xr-x 1 lance lance  302 Jul 20  2017 config #655

```

~/.ssh/config on both linux boxes
```

Host *
   User lance
   ForwardX11 yes
   IdentityFile ~/.ssh/id_rsa
   Compression yes

Host bermudezl
   HostName 192.168.2.3
   Port 22
   #LogLevel DEBUG1
   LogLevel VERBOSE
   Ciphers aes128-cbc,aes128-ctr,aes192-ctr,aes256-ctr

Host tardis
   HostName 192.168.2.5
   Port 22
   LogLevel VERBOSE

Host type40tardis
   HostName 192.168.2.9
   Port 22

```

---

### Post by lance bermudez on 2020-01-29
have even made new keys and it still does not work for type40tardis (192.168.2.9). and Yes this public key is in both linux boxes authorized_keys file

Now type40tardis (192.168.2.9) can not even ssh into its self 

ufw is turned off ~/.ssh is chmod 700 and Id_rsa is chmod 600 and Id_rsa.pub is chmod 644

```

$ ssh -vv 192.168.2.9
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.2.9" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.2.9 [192.168.2.9] port 22.
debug1: Connection established.
debug1: identity file /home/lance/.ssh/id_rsa type 0
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lance/.ssh/id_ed25519-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.2.9:22 as 'lance'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:zfZkRRE0MZ2+Haz9voe5pahSrGjIDK67KeKZ5Wnapnk
Warning: Permanently added '192.168.2.9' (ECDSA) to the list of known hosts.
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /home/lance/.ssh/id_rsa (0x55f301615170), agent
debug2: key: /home/lance/.ssh/id_dsa ((nil))
debug2: key: /home/lance/.ssh/id_ecdsa ((nil))
debug2: key: /home/lance/.ssh/id_ed25519 ((nil))
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:OMSMnblmKNOvbsfdVsT7jhICl9fitcbib2pF/oBbYwk /home/lance/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/lance/.ssh/id_dsa
debug1: Trying private key: /home/lance/.ssh/id_ecdsa
debug1: Trying private key: /home/lance/.ssh/id_ed25519
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
lance@192.168.2.9: Permission denied (publickey).

```

---

### Post by lance bermudez on 2020-01-30
Can not get this to work with key based authentication 
type40tardis (192.168.2.9) /etc/ssh/sshd_config
```

Port 22
# Authentication:
PermitRootLogin no
PubkeyAuthentication yes
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes
UsePAM no


```

working with key based authentication
tardis (192.168.2.5) /etc/ssh/sshd_config
```

Port 22
# Authentication:
PermitRootLogin no #prohibit-password

PubkeyAuthentication yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

UsePAM no

AllowAgentForwarding yes
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost no
PrintMotd no
PrintLastLog yes

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem	sftp	/usr/lib/openssh/sftp-server


```

---

### Post by lance bermudez on 2020-01-30
different key pairs on each linux box
```


~/.ssh$ ll
total 36
drwx------  3 lance lance 4096 Jan 29 21:48 ./
drwxrwxrwx 72 lance lance 4096 Jan 29 22:06 ../
-rw-------  1 lance lance 1138 Jan 29 21:47 authorized_keys
-rw-------  1 lance lance 3326 Dec 23  2018 id_rsa
-rw-r--r--  1 lance lance  744 Dec 23  2018 id_rsa.pub
-rw-r--r--  1 lance lance  666 Jan 29 21:48 known_hosts


```

---

