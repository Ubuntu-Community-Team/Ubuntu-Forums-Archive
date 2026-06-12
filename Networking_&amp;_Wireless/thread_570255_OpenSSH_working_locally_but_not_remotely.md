---
title: "OpenSSH working locally but not remotely"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by sinfony on 2007-10-08
I've been trying to configure OpenSSH so I can tunnel my VNC traffic in when I'm away from home, and I've had absolutely no luck.  Here's the situation: when I try to connect to my Ubuntu box from my Vista machine (using Putty) when both computers are on my home network, it works fine.  When I do the same remotely, I get the login prompt but every username/password combo returns an "Access Denied" message.  The same usernames/passwords work fine locally, and the fact that I even get the login prompt leads me to believe that there's no problem with my firewall, although I suppose that might not be the case.  Anybody have any ideas?

---

### Post by kevdog on 2007-10-08
Try connection with the -vv option, for example

ssh -vv .......

This will give you a very verbose output to further pin down the problem (you could even try -vvv)

---

### Post by sinfony on 2007-10-08
Here's the relevant part of my Putty log:
```
Event Log: Sent password
Incoming packet type 51 / 0x33 (SSH2_MSG_USERAUTH_FAILURE)
  ...
Event Log: Access denied
```

---

### Post by kevdog on 2007-10-08
So just to make sure -- you are using putty as the client and openssh on the Ubuntu box as the server.  You are using username/password rather than any key based authentication.

Can you post your /etc/ssh/sshd_config file here?  Can you attempt to telnet into port 22 or whatever port you are using.  This is one way to see if a firewall would be blocking you!!

---

### Post by hangthedj on 2007-10-08
> **sinfony said:**
> I've been trying to configure OpenSSH so I can tunnel my VNC traffic in when I'm away from home, and I've had absolutely no luck.  Here's the situation: when I try to connect to my Ubuntu box from my Vista machine (using Putty) when both computers are on my home network, it works fine.  When I do the same remotely, I get the login prompt but every username/password combo returns an "Access Denied" message.  The same usernames/passwords work fine locally, and the fact that I even get the login prompt leads me to believe that there's no problem with my firewall, although I suppose that might not be the case.  Anybody have any ideas?

you might check the /etc/ssh/ssh_config

i don't know that much about it, but there are a couple options like HostbasedAuthentication
CheckHostIP

also checkout /usr/etc/sshd_config

maybe those are set to yes, so its only letting your home network connect.

just a thought, like i said i don't know much about it.

---

### Post by sinfony on 2007-10-08
> **kevdog said:**
> So just to make sure -- you are using putty as the client and openssh on the Ubuntu box as the server.  You are using username/password rather than any key based authentication.

Can you post your /etc/ssh/sshd_config file here?  Can you attempt to telnet into port 22 or whatever port you are using.  This is one way to see if a firewall would be blocking you!!

Yes, I am using Putty as the client and openssh on my Ubuntu box as the server, using username/password instead of key-based auth.

Here's my sshd_config:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
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
PasswordAuthentication yes

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
UseLogin yes

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

When I try to telnet into port 22, I get the message "SSH-2.0-dropbear_0.43", which I find rather cryptic.

---

### Post by sinfony on 2007-10-10
No ideas?  Anybody?

Well, I'm switchign ISPs next week, I'll see if that makes any difference.

---

