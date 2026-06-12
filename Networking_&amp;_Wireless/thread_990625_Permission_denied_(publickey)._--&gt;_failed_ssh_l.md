---
title: "Permission denied (publickey). --&gt; failed ssh login"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by rocheteau on 2008-11-22
Hi, 
I have Ubuntu 7.04 installed (and upgraded) on my main machine and when I try to SSH in from my other Ubuntu machine I get the simple following error message:

Permission denied (publickey).

I have never experienced a problem with ssh in older versions of Ubuntu and as a result don't have much experience configuring the SSH server etc. I have spent a fair amount of time googling for this issue and found very little. I would have expected this to be a fairly common problem with more recent versions of Ubuntu. 
I would appreciate any help.
Thanks, 
R.

---

### Post by Iowan on 2008-11-22
I can't say I've had any problems logging onto a configured SSH server from another Ubuntu machine, either.  I still primarily use passwords, so the keys don't seem to cause issues.

---

### Post by ITAndrew on 2008-11-22
Remove your ~/.ssh/known_hosts file. Or just remove the entry for your host.

What is happening is your public key has changed, in other words ubuntu will not let you log on because it looks to be another machine (key is different). The above should fix it.

FYI this needs to be done on the box that you are attempting to connect to the remote machine on.

---

### Post by rocheteau on 2008-11-23
I tried what ITAndrew suggested (thanks for the suggestion) and got the following on the next attempt:

The authenticity of host '192.168.1.100 (192.168.1.100)' can't be established.
RSA key fingerprint is f7:99:4d:c6:9d:e5:3c:ac:11:e2:d4:db:3f:37:d3:d0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.100' (RSA) to the list of known hosts.
Permission denied (publickey).

So it proceeded as I have seen before but then fell back to the original error message. Is there any info, file contents etc that I should make available.

Thanks again for your help, 
R.

---

### Post by ITAndrew on 2008-11-23
What is in your /etc/ssh/ssh_config file

Also try ssh -v 192.168.1.100 and output the verbose log.

Also on the remote machine what is the output of the failed login from the log at /var/log/auth.log

Also on the remote machine, if you where to try to log in localy via ssh localhost does this happen as well?

---

### Post by ITAndrew on 2008-11-23
Forgot to throw this out there to, do you want to use public key authentication or just straight passphrase authentication?

If you want to use pub key auth you may want to give [http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/) a read. Otherwise we will keep at getting the passphase working for you.

---

### Post by rocheteau on 2008-11-23
I will answer ITAndrew's questions in order:

(1) The contents of my /etc/ssh/sshd_config file is:
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

(2) ssh -v 192.168.1.100 output is:
OpenSSH_4.3p2 Debian-8ubuntu1.5, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.100 [192.168.1.100] port 22.
debug1: Connection established.
debug1: identity file /home/rob/.ssh/identity type -1
debug1: identity file /home/rob/.ssh/id_rsa type 1
debug1: identity file /home/rob/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1.5
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.5
debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.100' is known and matches the RSA host key.
debug1: Found key in /home/rob/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rob/.ssh/identity
debug1: Offering public key: /home/rob/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/rob/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

(3) what is the output of the failed login from the log at /var/log/auth.log?
I don't see a log entry corresponding to the time of the failed login.

(4) When trying to log into the remote host locally i.e. localhost I get the following output (after first deleting known_hosts):
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is f7:99:4d:c6:9d:e5:3c:ac:11:e2:d4:db:3f:37:d3:d0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
Permission denied (publickey).

(5) Do you want to use public key authentication or just straight passphrase authentication?
My needs are pretty simple i.e. a small network in behind a commercial router. I would, however, like to learn as much as I can about the way this works i.e. I will read your suggested link. 

Once again I appreciate the time you are taking here, 
R.

---

### Post by ITAndrew on 2008-11-23
Not a problem, I think your problem lies in the sshd_config file. As I was looking at it I noticed you have the password autentication disabled.

> 
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no


This should probably be:

> 
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes


This allows text passwords to be sent back to the server for further authentication instead of a public key.

I can reproduce this on my machine.

Have a wonderful weekend!

---

### Post by ITAndrew on 2008-11-23
FYI, you will want to restart the service to by typing:

> sudo /etc/init.d/ssh restart

---

### Post by rocheteau on 2008-11-23
Thanks ITAndrew. Your suggestion worked and all is well. May I say one last time how much I appreciate your help. It's guys like you that keep the open source movement ticking (at least for less experienced users like myself). 
Thanks again, 
R.

---

### Post by rocheteau on 2008-11-23
A very quick follow-up: I had read that WinSCP had trouble logging into some machines running OpenSSH under later Ubuntu versions. I can now also log in with WinSCP after the change ITAndrew suggested. I'm not sure if there is another issue with WinSCP logins but in this case there is no problem.
Thanks again, 
R.

---

### Post by ITAndrew on 2008-11-23
Nope, they are one in the same. WinSCP passes the passphrase over plain text (yet still encrypted). So if the plain password was disabled WinSCP will fail to connect. ;-) The whole CLI interface will become easier to use over time, and you will gain a whole heck of a lot of knowledge along the way. Using Ubuntu make you a smarter person IMO.

---

