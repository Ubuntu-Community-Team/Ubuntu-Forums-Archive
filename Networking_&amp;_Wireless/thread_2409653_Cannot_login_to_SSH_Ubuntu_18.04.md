---
title: "Cannot login to SSH Ubuntu 18.04"
date: 2019-01-04
forum: Networking &amp; Wireless
---

### Post by HerzeleidMeister on 2019-01-04
Hello, I'm trying to login via SSH to my website on Bluehost. The site is already configured and works for SSH as I have already done a database backup prior to switching back to Ubuntu from Windows 10. I need to backup a particular database using SSH. Every time I try to login I get an "***Access Denied***" error.

**I've tried the following:**

1. Tried logging in using Putty. When I first installed Ubuntu I knew I would have to access my MySQL on Bluehost via SSH, so I installed it.
2. Tried logging in using "**OpenSSH**" after giving up on putty and installing it.
3. Tried editing "**/etc/ssh/sshd_config**" to allow port 22 & set "**AllowUsers**" to the user login for my Bluehost server. I also enabled "**PubkeyAuthentication yes**".

No matter what I've done I still get access denied. The password that I'm using is correct when I type it in. 

Any help would be greatly appreciated as I need this in order to work with client websites.

---

### Post by QIII on 2019-01-04
Hello!

Would you please post the *entire* message?

Also, if this server is exposed to the web, using a password for ssh access is extremely dangerous.  I'd never allow password access to my webservers over ssh.

Public key authentication can work at cross purposes with password authentication.  One or the other (key authentication is pretty much the rule if you want to keep from being pwned) is best.

---

### Post by HerzeleidMeister on 2019-01-05
The message was "Permission denied, please try again."

---

### Post by QIII on 2019-01-05
Was this from the terminal?

If so, please copy and paste the *entire* command and *entire* results in code tags.

---

### Post by HerzeleidMeister on 2019-01-05
Currently this is in the terminal. I've tried on Putty as well and go a permission denied message as well.

```
mylaptop@mylaptop-Lenovo-Y40-70:~$ ssh myserverloginname@xxx.xxx.xxx.xxx -p22 myserverloginname@xxx.xxx.xxx.xxx's password: 
Permission denied, please try again.
myserverloginname@xxx.xxx.xxx.xxx's password: 
```

---

### Post by Hadaka on 2019-01-05
Hi please try...
```
ssh -p22 myserver@xx.xx.xx.xx 
```
it should then prompt you for the password

Is the server on the same network as  the logging in computer ?
laptop 192.168.1.152...server  192.168.1.??
same router ?
are any ports forwarded ??
can you ssh in from any other machine ??

please provide that information.
thanks

---

### Post by QIII on 2019-01-05
Two things I see right off:


The preferred syntax is 

```
ssh -p <port> <username>@<ip>
```

There should be a space between "-p" and "22".

```
-p 22
```

Edit:  Since the default port is 22, I don't think you even need to specify that.

---

### Post by HerzeleidMeister on 2019-01-05
I made the adjustments did not work, I got the same thing. There has to be some sort of issue somewhere.

---

### Post by QIII on 2019-01-05
Do you have access to your machine via a control panel or the like?

---

### Post by Hadaka on 2019-01-06
@ QIII oops...thank you for the correction.

---

### Post by HerzeleidMeister on 2019-01-06
> **QIII said:**
> Do you have access to your machine via a control panel or the like?

I do not know what you mean. I'm on my laptop. The website is hosting with Bluehost. If you mean a control panel there, yes I do have access, but they do not have the built in cPanel backup installed. They have some sort of crappy backup system that does everything automatically that you cannot control, which for obvious reasons will not work. :(

---

### Post by QIII on 2019-01-07
Can you get to and log into your server through whatever form of control panel they offer?

Can you get to and copy your sshd_config file to paste it here (with any sensitive information redacted)?

---

### Post by HerzeleidMeister on 2019-01-07
Ok thought you were talking about the web page. That file is on my laptop I installed OpenSSH before all this.

```
#	$OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.


Port 22
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


PubkeyAuthentication yes


# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile	.ssh/authorized_keys .ssh/authorized_keys2


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
#UseLogin no
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
Subsystem	sftp	/usr/lib/openssh/sftp-server


# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	PermitTTY no
#	ForceCommand cvs server
AllowUsers mysitelogin.com
```

---

### Post by QIII on 2019-01-07
What is of interest is the sshd_config on the server, not the client you are connecting from.

The server's configuration is what controls access to it over SSH.

Or ar you saying you have a copy of the server's config on your laptop?

---

### Post by HerzeleidMeister on 2019-01-07
Sorry for any confusion, no there is no server on my laptop. I just actually fixed my problem. I was using the wrong login user name. I fixed that and it works just fine now.

---

