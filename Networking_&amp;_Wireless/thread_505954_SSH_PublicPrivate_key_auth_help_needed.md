---
title: "SSH Public/Private key auth help needed"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by scottgun on 2007-07-20
I have a server, gun1, that I SSH to from my laptop via cygwin.  I've been trying to get the public/private key authentication to work so that I can move toward a password-less log on.

First things first:  Both client and host have static IPs.  My ssh client 'config' file for the server is as follows:
```

Host gun1
Hostname 192.168.1.102
User scott
identityfile id_rsa

```

I generated the keys using ssh-keygen, appending  the *.pub file into /home/.ssh/authorized_keys on the server side.  Permissions for the folder are set according to the documentation.  The private key, id_rsa, resides in /home/.ssh on the client side.

Here is what happens when I try to log in:
```

$ ssh -v gun1
OpenSSH_4.5p1, OpenSSL 0.9.8d 28 Sep 2006
debug1: Reading configuration data /home/Scott Gunsaullus/.ssh/config
debug1: Applying options for gun1
debug1: Connecting to 192.168.1.102 [192.168.1.102] port 22.
debug1: Connection established.
debug1: identity file id_rsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.2p1 Debian-7ubuntu3.1
debug1: match: OpenSSH_4.2p1 Debian-7ubuntu3.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.102' is known and matches the RSA host key.
debug1: Found key in /home/Scott Gunsaullus/.ssh/known_hosts:12
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key 'id_rsa': ---------->I enter passphrase correctly
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```
Of course, password authentication works.  But it's disabled here, in order to illustrate the problem.  The full sshd_config file is available here, if that will be helpful.
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
PermitRootLogin no
AllowUsers scott
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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by mitch.c on 2007-07-23
> **scottgun said:**
> I have a server, gun1, that I SSH to from my laptop via cygwin.  I've been trying to get the public/private key authentication to work so that I can move toward a password-less log on.

First things first:  Both client and host have static IPs.  My ssh client 'config' file for the server is as follows:
```

Host gun1
Hostname 192.168.1.102
User scott
identityfile id_rsa

```

I generated the keys using ssh-keygen, appending  the *.pub file into /home/.ssh/authorized_keys on the server side.  Permissions for the folder are set according to the documentation.  The private key, id_rsa, resides in /home/.ssh on the client side.

Since you referenced cygwin, I am assuming your laptop is running Windows. I have a similar setup... my private key is stored in %userprofile%/.ssh/, with no identityfile option in the 'config' file.

According to the client config, you are logging on as 'scott', but you saved the public key on the remote host to /home/.ssh/authorized_keys. That won't work.

The public key should exist in /home/scott/.ssh/authorized_keys or /home/Scott Gunsaullus/.ssh/authorized_keys (I am assuming the latter is correct), or you need to change AuthorizedKeysFile in sshd_config at the remote host (not recommended).

Last piece of advice, use PuTTY and Pagaent on the Laptop.

Let me know if this helps.

---

