---
title: "ssh terminates first connection, refuses for about 15 secs then accepts and connects"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by Hilvar on 2006-11-17
Strangly annoying problem with Dapper.
Attempt to ssh to ubuntu box first has connection reset.
Subsequent attempts for the next 15 secs or so are refused.
Attempt to connect then succeeds and login and password can be entered.
Leave it alone for long enough - say 15 mins and go through the whole thing again but if you keep logging in then it is fine.
This is not a box I set up myself so I don't have the whole history on it but I am now in charge of getting this little niggle out of the box and it's being a pain.
Have tried connecting using PuTTY and Cygwin and it is the same.
Is also the same from two other machines. All machines connecting are XP SP2. Raw telnet to 22 also gets disconnected on first try - I'm having a hard time believeing it's not the server.
All ideas gratefully accepted. Thanks in advance.

---

### Post by Hilvar on 2006-11-17
As a followup to this ppl are experiencing similar types of behavior for VNC connections except they seem to be persisting a lot longer and an incorrectly terminated session is keeping users trying to reconnect but failing.
Anyone agree with me that it's starting to sound like the network stack has gone south?
Anyone had anything similar at all? I'm now disovering that the first machine was cloned from another one which having checked it also has the same problem :-(

---

### Post by dbott67 on 2006-11-17
I can't say that I've had any problems using VNC or SSH (my home desktop is Edgy & laptop is Dapper).  I frequently SSH or VNC from work (WinXP Pro using Putty) and never have any problems.

A few things to consider:

1. Is the server running iptables?
```
dbott@edgy:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

2. How is SSH configured to accept inbound connections?  Are you employing [TCP wrappers]("http://ubuntuforums.org/search.php?searchid=9879812") to deny/allow hosts? Or authorized keys?

Can you post the output of cat /etc/ssh/ssh_config and sshd_config:
```
dbott@edgy:/etc/ssh$ cat ssh_config
#       $OpenBSD: ssh_config,v 1.21 2005/12/06 22:38:27 reyk Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
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
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
```

```
dbott@edgy:/etc/ssh$ cat sshd_config
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
-Dave

---

### Post by dbott67 on 2006-11-17
Try logging in via SSH again and then check the auth.log file for the last few entries using the command **tail /var/log/auth.log**:

```
dbott@edgy:~$ tail /var/log/auth.log
Nov 17 10:17:01 edgy CRON[30757]: (pam_unix) session closed for user root
Nov 17 11:17:01 edgy CRON[32200]: (pam_unix) session opened for user root by (uid=0)
Nov 17 11:17:01 edgy CRON[32200]: (pam_unix) session closed for user root
Nov 17 12:17:01 edgy CRON[1175]: (pam_unix) session opened for user root by (uid=0)
Nov 17 12:17:01 edgy CRON[1175]: (pam_unix) session closed for user root
Nov 17 13:17:01 edgy CRON[2622]: (pam_unix) session opened for user root by (uid=0)
Nov 17 13:17:01 edgy CRON[2622]: (pam_unix) session closed for user root
[COLOR="Red"]Nov 17 15:17:39 edgy sshd[5615]: Accepted password for dbott from 24.244.YYY.ZZZ port 1441 ssh2
Nov 17 15:17:39 edgy sshd[5619]: (pam_unix) session opened for user dbott by (uid=0)[/COLOR]
Nov 17 15:18:23 edgy sudo:    dbott : TTY=pts/1 ; PWD=/home/dbott ; USER=root ; COMMAND=/sbin/iptables -L
```

---

