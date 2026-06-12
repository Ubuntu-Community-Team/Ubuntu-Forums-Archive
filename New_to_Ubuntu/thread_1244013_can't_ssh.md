---
title: "can't ssh"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by rgroene on 2009-08-19
I know I've got this working before on a different installation of ubuntu (in fact, I have it working right now on my old laptop), but it doesn't seem to be working right now on this one.

I simply want to be able to access my computer from another computer on the terminal via ssh. But whenever I do it, I get errors. When I try to ssh from another linux machine, I get the following error:

Read from socket failed: Connection reset by peer

When I try to connect from a Windows machine through PuTTY, I get:

Network error: Software caused connection abort

When I type "ssh localhost," I get:

warning: Need basic cursor movement capability, using vt100
warning: Authentication failed
Disconnected; connection lost (Connection closed)

I have installed ssh, openssh-server, and openssh-client.

---

### Post by prshah on 2009-08-19
> **rgroene said:**
> 
Read from socket failed: Connection reset by peer
Network error: Software caused connection abort

warning: Authentication failed
Disconnected; connection lost (Connection closed)


What kind of authentication are you using? Username / password? Or Public/Private key?

The first two errors seem to be a firewall problem; however, the last error may indicate some misconfiguration in your openssh server config; can you (obfuscate and) post your /etc/ssh/sshd_config file here?

Are you trying to ssh using the (LAN) ip address or the hostname?

---

### Post by rgroene on 2009-08-19
I think it's username/password. At least, when I've done it before on my other system, it's asked for username and password. In any case, it's whatever the default is after you install openssh-server.

I'm trying to ssh using the IP address. I'm pretty sure it's the right one because the one on my other machine is exactly the same except for one number. It's what comes up when I type ifconfig and look under eth1.

The file you requested is as follows:


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

---

### Post by rgroene on 2009-08-20
The file, by the way, is absolutely identical to the one on my other machine, which is working. So, I don't think that's the problem.

---

