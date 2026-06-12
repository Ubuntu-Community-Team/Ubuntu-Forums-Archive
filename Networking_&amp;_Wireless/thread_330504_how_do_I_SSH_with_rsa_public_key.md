---
title: "how do I: SSH with rsa public key"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-01-03
I want to connect from my work PC running WinXP with WinSCP to my home PC Ubuntu 6.06.

I used this link to get it working:

[http://doc.gwos.org/index.php/SecureSSH](http://doc.gwos.org/index.php/SecureSSH)

This is running fine, but I want to enhance security by using RSA public key, and this is explained quite sensibly here:

[http://doc.gwos.org/index.php/SecureSSH#Avoid_Using_Passwords](http://doc.gwos.org/index.php/SecureSSH#Avoid_Using_Passwords)

The problem is that it doesn't seem to work:  I do not need the public key on my WinXP box to connect to Ubuntu with WinSCP...it connects anyway despite having created an RSA key for my login and having copied it to the WinXP box and specified it in WinSCP...I never get prompted for the passphrase for the public key and if I remove it from WinSCP then I can still connect with normal user/pass combo...I do not want to be able to connect unless the public key is present.  Is there something missing from the link on the Document Storage Facility or have I misunderstood something?

---

### Post by xomix on 2007-01-03
What I understand:
winscp --> client
openssh --> server

2 problems: 
authentication only allowed with key (no password)
never prompt of passphrase

1.- Find a line in /etc/sshd/sshd_config that says:
PasswordAuthentication yes
and comment it out or change yes for no. Then restart the daemon with a kill -HUP or /etc/init/ssh restart

2.- Do you put the passphrase just once and then never again or not even once? I don't know winscp, but putty uses something called pageant. This is an ssh agent wich allows you to add a key at load, enter the passphrase only once and then putty looks for keys on this agent. I think that winscp brings pageant or it can use it. If you don't get asked for the passphrase at least once and you can connect only with the key, then the key has empty passphrase.

Hope that helps! ;)

---

### Post by finite9 on 2007-01-04
This is my config file...I still want to use an account password *as well as* a public key...can I not do both at the same time?

When I run the ssh-keygen program, it created some files in my ~/.ssh folder and it was this public key that I copied to the WinXP PC.

Regarding point 2...I never got prompted for the passphrase, as I had entered it in the WinSCP dialogue before first connection, but even if I do not specify the id_rsa.pub key in the connection properties then it still connects.  Even if the passphrase is saved, I have not given it a public key for connection, so it should not connect, right?

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by edafe on 2007-01-08
Here's some information on how to set up public/private key authentication with SSH:

[http://www.edafe.org/ubuntu/index.html#pubkey](http://www.edafe.org/ubuntu/index.html#pubkey)

Regards,
Edafe

---

