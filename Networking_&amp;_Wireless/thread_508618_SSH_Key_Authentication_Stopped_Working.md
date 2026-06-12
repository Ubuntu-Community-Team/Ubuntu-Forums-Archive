---
title: "SSH Key Authentication Stopped Working"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by oobogart on 2007-07-24
I've been using ssh to connect to my Ubuntu computer at home for months using key authentication.  Last Friday (7-20-07) I ran a software update and went to work.  I didn't pay attention to what was being updated .   When I got to work I tried to ssh into my Ubuntu box using putty.  I got a message "Server refused our key."  I've tried regenerating my key file and I've resorted to re enabling password authentication which I really didn't want to do.  Any help would be much appreciated.

---

### Post by dkirk on 2007-07-25
Do you get any error messages in /var/log/auth.log?

---

### Post by Mr. C. on 2007-07-25
Perhaps an update of sshd caused a new host key to be generated.  Try removing the existing host key in known_hosts, and reconnecting.

MrC

---

### Post by oobogart on 2007-07-25
I don't see any errors in my log to worry about.  The only errors I see are a few of these:

[INDENT]Jul 24 12:28:42 oobogart-desktop sshd[24442]: reverse mapping checking getaddrinfo for ext01.hertz.com failed - POSSIBLE BREAK-IN ATTEMPT!
[/INDENT]
I don't have a known_hosts file set up.  

Maybe I'm missing something.  Here is my sshd_config file:

[INDENT]# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 443
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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	~/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
# IgnoreUserKnownHosts yes

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
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes[/INDENT]

---

### Post by ushills on 2007-07-25
Try changing strictmodes to no, I had the same problem with keys not working until I did this.

---

### Post by oobogart on 2007-07-25
No go.

Any other logs I should be checking?

---

### Post by herbstr2408 on 2007-07-25
Hi,

[COLOR=Blue] >AuthorizedKeysFile    ~/.ssh/authorized_keys[/COLOR]

Does this file exist in your users .ssh directory ?

Also on my system (Ubuntu 7.04 Server) the entry in sshd_config looks like this,
(note the **%h**, instead of **~**)

[COLOR=Blue] AuthorizedKeysFile      %h/.ssh/authorized_keys2[/COLOR]

Dunno if that makes a difference though.

Rupert

---

