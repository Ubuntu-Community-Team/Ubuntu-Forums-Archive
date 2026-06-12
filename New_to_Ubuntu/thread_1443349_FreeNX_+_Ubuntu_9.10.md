---
title: "FreeNX + Ubuntu 9.10"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by wast3lanD on 2010-03-31
so when i try to access my ubuntu 9.10 freenx rigged lappy from my windoze axepee box i get this error:

```
NX> 203 NXSSH running with pid: 3260
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.5 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: matt
NX> 102 Password: 
NX> 103 Welcome to: lnxlapsrv user: matt
NX> 105 listsession --user="matt" --status="suspended,running" --geometry="1440x900x32+render" --type="unix-xdm"
NX> 127 Sessions list of user 'matt' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: matt
NX> 105 startsession  --xdm_port="-1" --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="ubuntuserverhome" --type="unix-xdm" --geometry="1024x768" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1024x768x32+render" 

**[COLOR=Magenta]Permission denied (publickey,password).[/COLOR]**
NX> 280 Exiting on signal: 15
```now that permission denied stuff right derr above is QUITE ANNOYING.

seeing that ive been working on this (freenx in general) for the past day, and there seems to be no tut's on fixing this issue, id really appreciate it if someone could help me out here :D

---

### Post by Peter09 on 2010-03-31
Can you confirm that you can login using ssh
 
```
ssh -X [EMAIL="username@machineid"]username@machineid[/EMAIL] 
```

---

### Post by wast3lanD on 2010-03-31
results of that command:

```
matt@lnxlapsrv:~$ ssh -X matt@lnxlapsrv
The authenticity of host 'lnxlapsrv (127.0.1.1)' can't be established.
RSA key fingerprint is cc:3b:98:6a:6b:a7:34:40:38:2f:83:5d:ef:36:cf:cf.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'lnxlapsrv' (RSA) to the list of known hosts.
matt@lnxlapsrv's password: 
Permission denied, please try again.
matt@lnxlapsrv's password: 
Permission denied, please try again.

```

so it appears as if the SSH password has been changed...
i used to ssh to this box all the time with PuTTY...

maybe it has something to do with the keys? i did regen keys using ./nxkeygen in the /nx/ folder, maybe that changed it. 

any suggestions?

---

### Post by Peter09 on 2010-03-31
Try the command like this

```
ssh -v user@machineid
```
to get more information

---

### Post by wast3lanD on 2010-04-01
Peter09:

sorry for the long wait, just finished up last week of college before spring break. 
i appreciate your help also

here is the output of the instructed command:

```
root@lnxlapsrv:~# ssh -vX root@lnxlapsrv
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to lnxlapsrv [127.0.1.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'lnxlapsrv' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
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
root@lnxlapsrv's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

```

---

