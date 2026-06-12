---
title: "slow ssh connection"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by indie_campbell on 2007-05-16
Hi,

I am having problems ssh into a server - it takes up to 20 seconds for the password prompt to appear. Here is the verbose output from the connection:

```
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/.ssh/identity ((nil))
debug2: key: /home//.ssh/id_rsa (0x80054508)
debug2: key: /home//.ssh/id_dsa ((nil))

```

connection hangs here before trying: 

```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home//.ssh/identity
debug3: no such identity: /home//.ssh/identity
debug1: Offering public key: /home/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home//.ssh/id_dsa
debug3: no such identity: /home//.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

```

the follow settings in the sshd_config have been set:
```
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
ChallengeResponseAuthentication no
UsePAM yes

#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
Subsystem       sftp    /usr/lib64/ssh/sftp-server

# This enables accepting locale enviroment variables LC_* LANG, see sshd_config(5).
AcceptEnv LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES
AcceptEnv LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT
AcceptEnv LC_IDENTIFICATION LC_ALL


```

Thanks

---

### Post by tjansson on 2007-08-14
I think it is a DNS problem - see this thread 
[http://ubuntuforums.org/showthread.php?p=3189998#post3189998](http://ubuntuforums.org/showthread.php?p=3189998#post3189998)

---

### Post by tenshimsm on 2008-01-16
The "UseDNS no" solved my slow ssh connection in both Feisty and Gutsy.
thanks to **tjansson** in 
this post [http://ubuntuforums.org/showthread.php?p=3189998#post3189998](http://ubuntuforums.org/showthread.php?p=3189998#post3189998)

---

