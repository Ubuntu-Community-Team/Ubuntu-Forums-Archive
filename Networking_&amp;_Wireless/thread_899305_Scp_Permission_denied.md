---
title: "Scp Permission denied"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by prats84 on 2008-08-24
Hi,
 I am trying to copy a file by Scp ... and but i get permission denied 

The commond i issue is :
  ```
 sudo scp -rv /etc/ldap/slapd.conf pratik@131.231.126.243:/etc/ldap 
```


Output is 
```
Executing: program /usr/bin/ssh host 131.231.126.243, user pratik, command scp -v -r -t /etc/ldap
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 131.231.126.243 [131.231.126.243] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '131.231.126.243' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
pratik@131.231.126.243's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug1: Sending command: scp -v -r -t /etc/ldap
Sending file modes: C0640 4829 slapd.conf
scp: /etc/ldap/slapd.conf: Permission denied
pratik@server-hen:~$ Sink: C0640 4829 slapd.conf
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
```




Thanks

---

### Post by prats84 on 2008-08-24
Does any1 have a vague idea about it...?

---

### Post by ilrudie on 2008-08-25
Yes.  You are trying to overwrite a root owned file with your user's permissions.  This won't work.  You need to scp it into your home directory, Then login to the server with ssh and use sudo cp to copy the file from your home directory into /etc/ldap.  Its also a good idea to make a backup of the existing file before copying over it.

---

### Post by prats84 on 2008-08-25
Alrite.... I ll try it out.... 


Thanks a lot

---

### Post by ssully on 2009-08-01
BTW, it's not a great idea to display your IP address online. :)

Cheers!

---

