---
title: "SSH security"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-07-19
I have a ssh server setup on my my with a passthough for port 22 on my router and an open port on my firehol firewall.

I have also installed fail2ban.

Are there any security considerations with this setup and is it secure, I usually have all ports stealthed so this is a bit new for me.  I understand I have to have the port open but should I do anything else.

---

### Post by djekels on 2007-07-19
if you are that paranoid, then you should probably configure ssh to work through tcp wrappers.

tcp wrappers has the ability to check the source IP and you can decide which Ip's are allowed to access your system by ssh.

---

### Post by p_quarles on 2007-07-19
One thing to do is open up /etc/ssh/ssh_dconfig and change ```
PermitRootLogin yes
``` to ```
PermitRootLogin no
```
Beyond that, you should make sure you have  a very strong password on the server system, considering installing and configuring Bastille Linux, and perhaps even change the port used for SSH.

Do you need to be able to access the machine via the Internet, though? If this is a home server that you only access via the local network, you probably don't need port 22 open on your router. Most router firewalls protect the network from traffic incoming over the broadband link, and don't block any ports requested via the LAN.

---

### Post by psyburn on 2007-07-19
You might want to set AllowedUsers to the login names you'll use.

Combine obscure login names with strong passwords and only one or two allowed ssh login names and I'd consider you secure enough if you watch your /var/log/auth.log to check for unwanted logins.

I allow password logins, so I'm not nearly as secure, but here is my config:

**/etc/ssh/sshd_config:**
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
PermitRootLogin no
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
IgnoreUserKnownHosts no
PasswordAuthentication yes
AllowUsers **[insert your allowed login names here]**
```

Any feedback BESIDES key auth would be welcome

---

