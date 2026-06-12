---
title: "OpenSSH Server connection doesn't work over LAN; times out"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Kalinda on 2008-04-28
Hello,

I've set up an OpenSSH server on one of my Linux boxes, but I can only connect to it on the machine itself and not from other machines; the connection always times out. This is strange because the SSH servers work on my brother's computer and my server, which runs Ubuntu Hardy Server Edition.

Since it works with the other machines, I'm fairly sure it isn't a problem with ports needing to be open on my router (this is for LAN only, anyway, not the outside world), so there's something wrong with just my setup. I haven't got any soft firewall apps running, either.

I have a static IP address, but so does one of the working machines.

Here's my sshd_config: 

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

I don't know too much about ports or anything, but maybe port 22 is being blocked on my computer somehow... how do I find that out?

Thanks!

---

### Post by SpaceTeddy on 2008-04-30
check the output of this command to see of the ssh server is really running
```
sudo netstat -lnp |grep 22
```

also, check the output of this command to see of your computer is dropping any pakets that you might need.
```
sudo iptables -L -vnx
```

if you are in doubt, paste the output here and i will have a look at it.

---

### Post by pitbullrd on 2008-05-01
Hi, im very new using ubuntu, i already install openssh, im having the same problem, when somebody try to connect does not work. connection times out.

it will be really helpfull if somebody post a howto of installing openssh server. thanks.

---

### Post by SpaceTeddy on 2008-05-02
openssh works out of the box - or so it always has for me - at least...
you install it, it starts itself, it works. There is no howto for it - or rather, it would consist of one line

```
sudo apt-get install openssh-server
```

if you cannot connect to the server, i'd suggest you check your firewall settings (firestarter ?) and make sure that the server port (22) is not taken by anything else with the commands from my previous posts :)

hope you get it to work :)

---

