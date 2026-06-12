---
title: "Help Uninstall SSH"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by dogbitedavehumphreys on 2009-09-15
Hello all,

Am having fun getting server on line for file sharing over internet, possible future website, have installed LAMP, SSH, Samba (running Windows LAN at work)

Anyway, have reinstalled server from CD about 5 times when I get in over my head and start over (I have no computer experience, really, at all and this is a major undertaking).

My problem this time is that I am locked out of putty by SSH authentication and would like to redo keys with Putty Generator in order to cut and paste keys into ssh_host key files because there is no way I am going to type that in without making a mistake.

Question :How can I unistall SSH and wipe out all changes I have made in ssh/sshd.confg so I can just start over on SSH?

Is there an easier way?

Thanks a million.

---

### Post by halitech on 2009-09-15
remove and reinstall ssh

```
sudo apt-get remove --purge openssh-server && sudo apt-get install openssh-server
```

I think this should be right

---

### Post by bacardiandwatermelon on 2009-09-15
Good luck with the ssh, here is a copy of my sshd_config file... ```
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
PermitRootLogin no
StrictModes no

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication no

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
```This site may help ya a little bit too....
[http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

---

### Post by dogbitedavehumphreys on 2009-09-15
Halitech,

Thank you so much.

This worked when I did the remove/purge and get/install separately remove first, install second, for some reason (probably operator induced).

Cheers, 

Dave

---

