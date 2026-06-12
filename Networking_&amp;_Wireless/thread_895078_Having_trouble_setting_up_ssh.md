---
title: "Having trouble setting up ssh"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by pablo66 on 2008-08-19
I loaded openssh-server on the machine I intend as the server and ran ```
paul@paul-desktop:~$ ssh localhost
``` and generated keys and
that seems fine. On the machine that I want to use to connect to the server(laptop), I installed openssh-client and then did ```
paul@paul-laptop:~$ ssh localhost
ssh: connect to host localhost port 22: Connection refused

```

How do I open this port? Or verify which ports are open?

Laptop is running Ubuntu, and server is running Xubuntu both 8.04, connecting them is a linksys wireless-G router.

Thanks in advance,

---

### Post by dmizer on 2008-08-19
On the desktop, have you installed openssh-server?
```
sudo aptitude install openssh-server
```

Are you running firestarter on the desktop? Do you have an iptables configuration implemented?

To find out, run this command:
```
sudo iptables -L
```

---

### Post by pablo66 on 2008-08-19
Yes, and when I run localhost I'm promted for my password and I have access.

---

### Post by pablo66 on 2008-08-19
I have not loaded ssh-server on the laptop that I'm having a problem with, only ssh-client.

---

### Post by dmizer on 2008-08-19
> **pablo66 said:**
> I have not loaded ssh-server on the laptop that I'm having a problem with, only ssh-client.

Unless you have a custom install, ssh-client is a part of the standard Ubuntu packages. Also, there is no need to install the server on a client.

Do you have iptables configured on the desktop?

---

### Post by pablo66 on 2008-08-19
when I run ```
sudo iptables -L
``` I get

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by dmizer on 2008-08-19
From the desktop, please post the contents of this file: /etc/ssh/sshd_config

---

### Post by pablo66 on 2008-08-19
no, I don't have iptables configured on the desktop

---

### Post by pablo66 on 2008-08-19
contents of ssh/sshd_config ```
Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

### Post by dmizer on 2008-08-19
The above post was from ssh_config, not sshd_config

---

### Post by pablo66 on 2008-08-19
OOps!! you're right!!, sorry about that
```
paul@paul-desktop:/etc/ssh$ more sshd_config
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

### Post by jimv on 2008-08-19
How did no one notice this?  He's trying to SSH into the server by typing "ssh LOCALHOST" on the laptop.

"Localhost" refers to whatever computer you are using at that moment.  You need to type in the ip address of the server...so it will be something like:

ssh 192.168.x.x

You can get the ip address of the server by typing "ifconfig" on the server.

---

### Post by dmizer on 2008-08-19
> **jimv said:**
> How did no one notice this?

He's trying to SSH into the server by typing "ssh LOCALHOST" on the laptop.

You need to type in the ip address of the server...so it will be something like:

ssh 192.168.x.x

You can get the ip address of the server by typing "ifconfig" on the server.

:oops:

Where's my brain today.  That's quite right.

---

