---
title: "Unable to ssh-copy-id from ARM client to X86 server"
date: 2022-02-24
forum: Networking &amp; Wireless
---

### Post by foxsquirrel on 2022-02-24
ssh into the server works fine however, have not been able to use nautilus from the client to access server using sftp. Just discovered ssh-copy-id hangs up after password request from server

server: 5.13.0-28-generic #31-Ubuntu SMP Thu Jan 13 17:41:06 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

client: 4.9.241 #24 SMP PREEMPT Sat Jan 8 13:20:29 CST 2022 aarch64 aarch64 aarch64 GNU/Linux


The nautilus issue has been chronic with many different kernels and versions 20.04 & 21.10 (all ARM). Can ssh in fine and nautilus can log into a SMB share fine just not sftp or copy-id to server. It takes crl-z to exit the hang up in a terminal.

This is on a VIM3 and Pi4b clients

Dell server

How do I determine if its the server or clients?
What logs if any would be helpful?


UFW on server:

To                         Action      From
--                         ------      ----
Apache Full                ALLOW       Anywhere                  
OpenSSH                    ALLOW       Anywhere                  
123/udp                    ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                   (log)
Samba                      ALLOW       Anywhere                  
Apache Full (v6)           ALLOW       Anywhere (v6)             
OpenSSH (v6)               ALLOW       Anywhere (v6)             
123/udp (v6)               ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6)              (log)
Samba (v6)                 ALLOW       Anywhere (v6)

---

### Post by TheFu on 2022-02-25
Does **ssh -vvvv** show anything useful?
Are the identity files standard or custom?

Can you post the exact ssh-copy-id command, options and output?  Please?
If the permissions for the file that ssh-copy-id is incorrect, there can be issues. It needs to be closed, but open enough.

Is sftp-server configured?  It should be in Ubuntu, but I cannot speak for other OSes.

---

### Post by foxsquirrel on 2022-02-25
> Does **ssh -vvvv** show anything useful? > no



```
xxxxx@xxxxx:~$ ssh-copy-id xxxxxxx
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/xxxxx/.ssh/xxxxxx.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
###############################################################
#       ALERT! You are entering into a secured area!
#
#
###############################################################
#Your IP, Login Time, Username has been noted and has been
#sent to the server administrator!
#
#
#This service is restricted to authorized users only.
#
#All activities on this system are logged.
#Unauthorized access will be fully investigated and
#reported to the appropriate law enforcement agencies.                                
#                                  
#                       
###############################################################
xxxxx@xxxxxx password:

```
That is as far as it goes then hangs after entering the password.

> Is sftp-server configured?
Assuming its working because Filezilla is able to connect and transfer files with sftp port 22 between win 10 and x86 ubuntu and ARM64

It might be the server is not configured properly since the Win 10 boxes can only connect to samba share folders.



server ssh_config

```
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

Include /etc/ssh/ssh_config.d/*.conf

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
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
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
```

this is Ubuntu 20.04 LTS server

---

### Post by foxsquirrel on 2022-02-27
Just confirmed it is the server config issue not the clients. Took a VIM3 to our other location and tried it on a test server and it works fine so the problem is with the server configuration.

---

### Post by TheFu on 2022-02-27
ssh_config is the client config file.  You need the ssh[COLOR="#FF0000"]d[/COLOR]_config for the server.
I've asked for a few things. Not going to be provided?

---

### Post by foxsquirrel on 2022-02-27
```
       $OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Include /etc/ssh/sshd_config.d/*.conf

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#PubkeyAuthentication yes

# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile     .ssh/authorized_keys .ssh/authorized_keys2

#AuthorizedPrincipalsFile none

#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none

# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
#       ForceCommand cvs server

```

> Are the identity files standard or custom?
standard

---

### Post by foxsquirrel on 2022-02-27
Just put it back on wire and it works. For some reason it is having  an issue with Wifi.

---

