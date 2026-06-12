---
title: "X-session via SSH?"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by roots on 2005-08-22
hi everybody,

i got my notebook (1) running on hoary and another machine (2) in our lan on suse9.2.

now, when i connect from (1) to (2) via

```
ssh -X ipaddress_of_(2)
``` 

and then, through this connection, try to open an application on (2) that has a gui (that i want to see on (1)), i do get the error message

```
app: cannot connect to X server 
```

it worked before, when i had (1) running on suse as well, but as i'm pretty n00b to ubuntu - can anyone help?


cheers,
.roots

---

### Post by tonym on 2005-08-22
In your ssh session,  is the DISPLAY environment variable set?

Assuming it isn't,  try logging in using -vX  .  This will give you some diagnostic info that may help.

---

### Post by roots on 2005-08-22
um, using the -vX option, i do get

```
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.x [192.168.0.x] port 22.
debug1: Connection established.
debug1: identity file /home/roots/.ssh/identity type -1
debug1: identity file /home/roots/.ssh/id_rsa type -1
debug1: identity file /home/roots/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_3.7.1p2
debug1: match: OpenSSH_3.7.1p2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.x' is known and matches the RSA host key.
debug1: Found key in /home/roots/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/roots/.ssh/identity
debug1: Trying private key: /home/roots/.ssh/id_rsa
debug1: Trying private key: /home/roots/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
``` 

another point is, should i be concerned about

```
ps aux | grep X
``` 
```
root      5995  2.6  5.7  34160 28584 ?        S    11:21   3:54 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
``` 

btw. about the "nolisten..." thing? could this be the problem?

cheers,
.roots

---

### Post by roots on 2005-08-22
ok, problem solved. i made a stupid mistake i'm not gonna mention here ;-)

cheers,
.roots

---

