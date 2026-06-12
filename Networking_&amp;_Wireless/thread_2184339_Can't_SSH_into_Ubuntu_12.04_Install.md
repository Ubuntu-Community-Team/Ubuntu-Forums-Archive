---
title: "Can't SSH into Ubuntu 12.04 Install"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by Mr. Snuggles on 2013-10-28
I'm having problems logging into a 12.04 desktop with SSH, from *within* the local network. Attempt results in:

```
>ssh -vv user@xxx.xx.xxx.xxx
OpenSSH_4.3p2, OpenSSL 0.9.8e-fips-rhel5 01 Jul 2008
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xx.xxx.xxx [xxx.xx.xxx.xxx] port 22.
debug1: connect to address xxx.xx.xxx.xxx port 22: Connection timed out
ssh: connect to host xxx.xx.xxx.xxx port 22: Connection timed out


```


I have been using linux for a while now, so here is what I understand to be the pertinent information:

I CAN ping the system.

Openssh-server is installed and SSHD IS running.

There are NO firewall rules active (ufw or iptables).

I CAN login to the localhost.

Port 22 IS open and listening.

```
>nmap -sV -p 22 xxx.xx.xxx.xx

Host is up (0.000025s latency).
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 5.9p1 Debian 5ubuntu1.1 (protocol 2.0)

>sudo ss -lnp | grep sshd

LISTEN     0      128                      :::22                      :::*      users:(("sshd",28768,4))
LISTEN     0      128                       *:22                       *:*      users:(("sshd",28768,3))

```

Below is the sshd_config file (default settings from clean openssh-server install):

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
```

And the strange thing is, on the same computer with a RHEL6 install, everything works fine.

Anything I am doing wrong and/or missing?

---

### Post by papibe on 2013-10-28
Hi Mr. Snuggles.

I'm a little confused. From your first code snippet, it looks like you're having problems connecting to a Red Hat machine:
```
OpenSSH_4.3p2, OpenSSL 0.9.8e-fips-[COLOR="#FF0000"]**rhel5**[/COLOR] 01 Jul 2008
```
Since an Ubuntu machine would respond something like:
```
OpenSSH_5.3p1 [COLOR="#0000FF"]**Debian-3ubuntu7**[/COLOR], OpenSSL 0.9.8k 25 Mar 2009
```
Regards.

---

### Post by Mr. Snuggles on 2013-10-28
Sorry, that is a bit unclear. The first code is my attempt to login *to* the Ubuntu machine *from* a RHEL machine on the same local network. The reverse works fine; I can SSH into said RHEL machine from the Ubuntu install, but not vice versa.

---

### Post by papibe on 2013-10-28
Thanks.

A few ideas.

Are you able to connect physically to the Ubuntu machine? If so, could you try ssh into itself, both to localhost and then to its network name?

Could you also post an attempt from RedHat to Ubuntu using the triple verbose option?
```
sh **-vvv** user@xxx.xx.xxx.xxx
```
Also, is there any firewall setting on the RedHat machine that would stop the connection from going out?

Regards.

---

### Post by Mr. Snuggles on 2013-10-28
> **papibe said:**
> Thanks.

A few ideas.

Are you able to connect physically to the Ubuntu machine? If so, could you try ssh into itself, both to localhost and then to its network name?

Could you also post an attempt from RedHat to Ubuntu using the triple verbose option?
```
sh **-vvv** user@xxx.xx.xxx.xxx
```
Also, is there any firewall setting on the RedHat machine that would stop the connection from going out?

Regards.

SSH into both localhost and network name works correctly from the Ubuntu machine.

Triple verbose gives the same output as double verbose.

I can SSH into the problem system just fine when it is booted into RHEL, so firewall (in the other red hat machine) shouldn't be a problem.

---

### Post by papibe on 2013-10-28
If you are dual booting, and keeping the same hostname you should be getting the [NASTY ERROR]("https://kb.mediatemple.net/questions/136/SSH+known_hosts+issues"). However, the error may be occurring even before even checking the SSH server key.

What is the content of your Ubuntu's /etc/hosts.allow and /etc/hosts.deny ?

Regards.

**EDIT**: I run some tests, and the only way I can reproduce the exact log from -vvv is when ssh is either not installed or not running. I'd recommend to double check your openssh-server installation on Ubuntu.
To restart the server:
```
sudo service ssh restart
```
You may want to uninstall and reinstall:
```
sudo apt-get purge openssh-server
sudo apt-get update
sudo apt-get install openssh-server
```
Regards.

---

### Post by Mr. Snuggles on 2013-10-29
> **papibe said:**
> If you are dual booting, and keeping the same hostname you should be getting the [NASTY ERROR]("https://kb.mediatemple.net/questions/136/SSH+known_hosts+issues"). However, the error may be occurring even before even checking the SSH server key.

What is the content of your Ubuntu's /etc/hosts.allow and /etc/hosts.deny ?

Regards.

**EDIT**: I run some tests, and the only way I can reproduce the exact log from -vvv is when ssh is either not installed or not running. I'd recommend to double check your openssh-server installation on Ubuntu.
To restart the server:
```
sudo service ssh restart
```
You may want to uninstall and reinstall:
```
sudo apt-get purge openssh-server
sudo apt-get update
sudo apt-get install openssh-server
```
Regards.

I do get the NASTY error on a fresh install of openssh-server, but remove/regen of the key fixes that. I rarely boot into the RHEL install, so in practice this isn't a problem.

Unfortunately, I've tried numerous re-installs (including purge), and the problem persists. Restarting the ssh service is similarly ineffective.

The contents of hosts.allow:

```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
sshd: ALL : ALLOW
```

And hosts.deny:

```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

---

### Post by Mr. Snuggles on 2013-10-29
Found the problem. Turns out Firestarter was running and blocking incoming connections. Very strange as I have no recollection of ever installing Firestarter.

Thanks for the help, papibe. Looks like I need to be more thorough with my troubleshooting next time.

---

### Post by papibe on 2013-10-29
No problem ;)

Sometimes just talking about a problem helps yourself to solve it on your own ):P

---

