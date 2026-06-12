---
title: "SSH remote access problem"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by djmac on 2010-02-24
I am trying to use SSH to remotely access my desktop from my laptop.

At present, I have had success accessing it from the local network (I have already set up static IP's etc, works perfect every time).

 However, when I attempt to connect using my stationary IP (where xxx.xxx.xxx.xxx is my stationary IP, set by ISP), I have no luck what so ever:

```
user@user-laptop:~$ ssh user@xxx.xxx.xxx.xxx
user@xxx.xxx.xxx.xxx's password:
Permission denied, please try again. 
user@xxx.xxx.xxx.xxx's password:
Permission denied, please try again.
user@xxx.xxx.xxx.xxx's password:
Permission denied (publickey,password).

```

(It asks for password three times though, before the permission denied message)

I am fairly confident that I have set up port forwarding (of port 22) in my router too. (My guess is that it wouldn't get as far as ask for my password if I hadn't?)

Any thoughts or suggestions would be great!

Thankyou

---

### Post by kwacka on 2010-02-24
I suspect you haven't activated public keys.

See [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by undecim on 2010-02-24
You're not accidentally connecting to someone else's server, are you?

Also, check caps lock, and your username.(if your username is thesame on both the client and server, you can omit the "user@" part)

---

### Post by djmac on 2010-02-24
I checked the shh configuration file (/etc/ssh/sshd_config) and I am pretty sure the public key authorisation is on:

```

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys
```

Also I triple checked my IP (I originally thought that I accidentally  connected to someone else's server too!. I think it would pretty amazing/coincidental if some random person had the same user name as me!

I don't have any problems logging in over the internal network, so I don't think it is a password mistake.

Thanks

---

### Post by undecim on 2010-02-24
Can you run ssh with "-vv" and post the output?

Also try setting up public key authentication. The link in kwacka's post has instructions (but you should leave out the "-t dsa" part in ssh-keygen)

---

### Post by djmac on 2010-02-24
I think I have already done that actually. When I attempt to connect locally, it asks for the passphrase to my private key.

The output of ssh -vv when I try to connect remotely is:

```
user@user-laptop:~$ ssh user@xxx.xxx.xxx.xxx -vv
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.xxx.xxx [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.46
debug1: no match: dropbear_0.46
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
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
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 205/384
debug2: bits set: 521/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host 'xxx.xxx.xxx.xxx' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:3
debug2: bits set: 480/1024
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
debug2: key: /home/user/.ssh/id_rsa (0x2af5a60)
debug2: key: /home/user/.ssh/identity ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password

```

---

### Post by bodhi.zazen on 2010-02-24
Well you are connecting and the system is asking for your log in password.

If you are using a key, what is the name of the key ?

You specify a key with the -i option

ssh -i ~/.ssh/name_of_key user@server

Either that or there is a problem with the key. Did you edit it in some way ?

---

### Post by djmac on 2010-02-25
I tried that:

```
user@user-laptop:~$ ssh -i ~/.ssh/id_rsa.pub user@xxx.xxx.xxx.xxx

```

And got the same permission denied error. I don't believe I have messed with the key. (It does work when I log on from the local network if that is any help?)

Thanks

---

### Post by bodhi.zazen on 2010-02-25
should be id_rsa not id_rsa.pub

The .pub key goes on the server.

Can you log in with a password , or did you disable passwords ?

---

### Post by djmac on 2010-02-25
I tried that too, to no avail. I can not log in using password remotely (I can from the local network)

---

### Post by ukripper on 2010-02-25
Check you port forwarding on router and iptables firewall on your server (not set to block external ips outside your LAN). most probably it is firewall on server.

---

### Post by djmac on 2010-02-27
This is the out put of # iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

(That is on the server desktop too)

---

### Post by ukripper on 2010-03-01
post your sshd_config here. And from external network try this website and see if port is forwarded correctly to your ssh server

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

---

### Post by djmac on 2010-03-03
According to the website [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) the port is open. 

I just got a new message, when I tried to login:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
e7:8e:dd:b6:b8:62:8f:2e:f2:46:c8:6e:73:a9:3c:f4.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:1
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
```

Hopefully this may be useful?

---

### Post by undecim on 2010-03-03
> **djmac said:**
> According to the website [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) the port is open. 

I just got a new message, when I tried to login:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
e7:8e:dd:b6:b8:62:8f:2e:f2:46:c8:6e:73:a9:3c:f4.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:1
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
```

Hopefully this may be useful?

Did your IP change? It seems that either you are connecting to another machine, or someone is trying to eavesdrop on your traffic.

---

### Post by djmac on 2010-03-03
This is the sshd_config for the client (i.e. my laptop)

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
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
#PasswordAuthentication yes

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

UsePAM yes
```

---

### Post by undecim on 2010-03-03
> **djmac said:**
> This is the sshd_config for the client (i.e. my laptop)

The sshd_config shouldn't matter on the client, just the ssh_config.

You need the sshd_config from the server.

---

### Post by djmac on 2010-03-03
. . . . And this is for the server (i.e. my desktop)

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
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
#PasswordAuthentication yes

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

UsePAM yes
```

Hope that helps!

---

### Post by djmac on 2010-03-03
> Did your IP change? It seems that either you are connecting to another machine, or someone is trying to eavesdrop on your traffic.

IP is the same . . .  I tried logging in from a different IP than the other times (should that matter though?)

---

### Post by undecim on 2010-03-03
> **djmac said:**
> IP is the same . . .  I tried logging in from a different IP than the other times (should that matter though?)

Just to make sure, can you run this command from the server?

```
ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub
```

You should get something in this format:
```
2048 XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX /etc/ssh/ssh_host_rsa_key.pub (RSA)
```

Does the XX:..:XX part match the fingerprint from the error message?

---

### Post by djmac on 2010-03-03
> **undecim said:**
> 

Does the XX:..:XX part match the fingerprint from the error message?

Yeah it does.

---

### Post by undecim on 2010-03-03
> **djmac said:**
> Yeah it does.

Perhaps you were somehow. connecting to the wrong machine before? Or if this happens when you connect locally also, then your host key just changed is all.

If this only happens when connecting from the internet, you should probably change your password, since you typed that password onto someone else's machine before.

If the fingerprints match it should be fine to remove line 1 from .ssh/known_hosts on the client, then try to connect again.

---

### Post by deepm718 on 2013-04-13
> **djmac said:**
> I am trying to use SSH to remotely access my desktop from my laptop.

At present, I have had success accessing it from the local network (I have already set up static IP's etc, works perfect every time).

 However, when I attempt to connect using my stationary IP (where xxx.xxx.xxx.xxx is my stationary IP, set by ISP), I have no luck what so ever:

```
user@user-laptop:~$ ssh user@xxx.xxx.xxx.xxx
user@xxx.xxx.xxx.xxx's password:
Permission denied, please try again. 
user@xxx.xxx.xxx.xxx's password:
Permission denied, please try again.
user@xxx.xxx.xxx.xxx's password:
Permission denied (publickey,password).

```

(It asks for password three times though, before the permission denied message)

I am fairly confident that I have set up port forwarding (of port 22) in my router too. (My guess is that it wouldn't get as far as ask for my password if I hadn't?)

Any thoughts or suggestions would be great!

Thankyou



Hi,

The 1st thing you should go to your home dir. & see user list with ls command, now u can see all users Ex.(cd /home/    NOW putt command ls) here display all users.
Now on that system where you from you want to access remotely, put command ssh user(listed in home dir.)@remote_host_ip_address, hitt Enter.
Now give that user's password who listed in home dir.. 
i'm sure you can access.
(IT MAY BE REQUIRED FOR SUPER USER PERMISSIONS... SO YOU NEED TO PERMIT IT)

---

### Post by oldos2er on 2013-04-13
Closed, please don't bump old threads.

---

