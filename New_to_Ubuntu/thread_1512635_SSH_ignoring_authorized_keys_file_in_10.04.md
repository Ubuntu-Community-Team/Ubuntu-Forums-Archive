---
title: "SSH ignoring authorized_keys file in 10.04"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Blond_Knight on 2010-06-18
Hello Guys hoping somebody can help me out with this.
I want to only allow ssh to my server from a machine that has the RSA key.
So I create the key:
> ssh-keygen -t rsa
Accept the default filenames and locations, my .ssh folder.
Rename the id_rsa.pub file to authorized_keys
I uncommented the line in the sshd_config file:
> #AuthorizedKeysFile      %h/.ssh/authorized_keys

And restart ssh
> sudo /etc/init.t/ssh restart

Now Im thinking that at this point I shouldnt be able to ssh into the box until Ive exported and setup the private key.  But Im able to successfully login.  And Ive tried this both on my home server 10.04 and a work VM thats also 10.04.  And I just did this yesterday on a ZixVPM box that worked as expected.
I also tried changing the permissions on the authorized_keys file to only I had read access, then only so root had access, restarting ssh each time.
Except for uncommenting the authorizedkeysfile line the sshd_config file is the default.  
Is it broken or am I missing something obvious? 
Thanks Guys.

---

### Post by Brandon Williams on 2010-06-18
You shouldn't need to uncomment the AuthorizedKeysFile line in the config, since that represents the default. On the other hand, you probably do need to set both ChallengeResponseAuthentication and PasswordAuthentication to 'no' in order to disable those login methods.

---

### Post by CharlesA on 2010-06-18
Here's my sshd_config file:

```
charles@thor:~$ cat /etc/ssh/sshd_config
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
LoginGraceTime 30
PermitRootLogin no
StrictModes yes

RSAAuthentication no
**PubkeyAuthentication yes**
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
#PasswordAuthentication no

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

#MaxStartups 3:50:10
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
AllowUsers charles
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes
IgnoreUserKnownHosts no
**PasswordAuthentication no**
```

---

### Post by Blond_Knight on 2010-06-18
Thanks for the quick responses guys.  Yes I figured out I had to uncomment PasswordAuthentication and set its value to no.

Hmm interesting I didnt know that authorized_keys was the default and you didnt have to uncomment it.

---

