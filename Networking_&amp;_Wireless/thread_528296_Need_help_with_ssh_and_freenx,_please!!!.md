---
title: "Need help with ssh and freenx, please!!!"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by hsalgado on 2007-08-17
I am having big troubles configuring freenx and I probably messed out the ssh configuration. I can not "ssh localhost", I get "Permission denied (publickey)".  This is what I get from ssh -vvv localhost:
```

OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/salgado/.ssh/identity.
debug1: identity file /home/salgado/.ssh/identity type 2
debug1: identity file /home/salgado/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/salgado/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
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
debug1: identity file /home/salgado/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

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
debug2: dh_gen_key: priv key bits set: 134/256
debug2: bits set: 521/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/salgado/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 9
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/salgado/.ssh/known_hosts:9
debug2: bits set: 522/1024
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
debug2: key: /home/salgado/.ssh/id_dsa (0x800599d0)
debug2: key: /home/salgado/.ssh/id_dsa (0x800596b8)
debug2: key: /home/salgado/.ssh/identity (0x80054630)
debug2: key: /home/salgado/.ssh/id_rsa ((nil))
debug2: key: /home/salgado/.ssh/id_dsa (0x80054510)
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/salgado/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering public key: /home/salgado/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering public key: /home/salgado/.ssh/identity
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/salgado/.ssh/id_rsa
debug3: no such identity: /home/salgado/.ssh/id_rsa
debug1: Offering public key: /home/salgado/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

This is my sshd_config file:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes no

#RSAAuthentication yes
#PubkeyAuthentication yes
AuthorizedKeysFile	~/.ssh/authorized_keys
AllowUsers nx salgado

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
 PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no 
```

Please, help me.  I need to make this work to be able to access my machine from the university.  Thanks a lot!!!

---

### Post by gerasmus on 2007-08-17
There is a MUCH easier version then FreeNX to install and use. requires virtually NO setup config.
Download the NXclient, node and server from [www.nomachine.com](www.nomachine.com)  onto your 'server'.
next thing is that you install the NXclient for Windows or Linux on your machine. Start the client, type IP address of remote machine, and you're connected. As simple as that. offcourse you can set additional encryption keys, SSH keys etc if you want as well.  Using NX you can have a remote access within less than 10 minutes.

---

### Post by hsalgado on 2007-08-17
Thanks a lot for your answer.  Yes, that is the program I am having problems with.  It uses ssh connection, but I can not log into my machine using ssh...   I think I need to solve the ssh problem to be able to use nomachine NX (which is the "freeNX" part of my post).   Thanks a lot anyway.

---

### Post by kevdog on 2007-08-17
Delete, remove or comment out the AllowUsers  line in the sshd_config file.

---

### Post by hsalgado on 2007-08-17
I did it but it still says "Permission denied (public key)"... is there a way of reinstalling the public key?  Thanks for your help!

---

### Post by kevdog on 2007-08-17
In the .ssh directory delete id_rsa id_rsa.pub and authorized_keys.

Then
ssh-keygen -t rsa -b2048

Im not at my computer right now, but I think it will spit out a id_rsa (private key) and id_rsa.pub (public key).  

cat id_rsa.pub > authorized_keys

It should be something like that --- Im not in the position I can test everything right now!

---

### Post by Mr. C. on 2007-08-17
Your config is not finding an id_rsa file, but is finding a id_dsa file:

```
debug1: identity file /home/salgado/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/salgado/.ssh/id_dsa.
```

Did you create RSA or DSA keys ?  You probably want RSA.

MrC

---

### Post by hsalgado on 2007-08-17
I FOUND THE PROBLEM!!!! I can't believe it... I wrote AuthorizedFiles **~**/.ssh/something and it should have been **%h**/.ssh/something!!!! Now I can ssh to the machine!  Thanks a lot for all your time!

---

### Post by punkybouy on 2007-08-26
Can you be more specific?  Authorized where?  .ssh/something what?

---

### Post by kevdog on 2007-08-26
I think he meant that within the /etc/ssh/sshd_config file under the line stating
AuthorizedKeysFile 
he made the appropriate modifications.

---

