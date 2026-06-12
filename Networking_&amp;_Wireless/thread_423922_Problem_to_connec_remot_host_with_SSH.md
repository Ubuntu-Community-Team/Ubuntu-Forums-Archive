---
title: "Problem to connec remot host with SSH"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by chacham23 on 2007-04-26
I tried like this:
```

root@assaf-desktop:/etc# ssh ******@leeware.com -l root
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive). 

```
I succeed in log in with windows and i know the problem is on my computer... someone can help me???
I work on Ubuntu 7.1 **(awesome!!!!!!!)** 

here is my **sshd_config**:

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
#AuthorizedKeysFile   %h/.ssh/authorized_keys

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

thanks in advance

---

### Post by chacham23 on 2007-04-26
up... some one?

---

### Post by .rdg on 2007-04-26
That's what I don't get:

ssh ******@leeware.com -l root

If the asterisks are your user-name on the leeware.com server (that's where you connect), then the command should look like:

ssh -l ****** leeware.com

You only use -l if your currently used user (in the example you shown it's root) is not the same you want to connect with.

Additionally - security wise - you should disable the root login via ssh (PermitRootLogin no in sshd_config). It's not wise to allow it.

---

### Post by chacham23 on 2007-04-26
> **.rdg said:**
> That's what I don't get:

ssh ******@leeware.com -l root

If the asterisks are your user-name on the leeware.com server (that's where you connect), then the command should look like:

ssh -l ****** leeware.com

You only use -l if your currently used user (in the example you shown it's root) is not the same you want to connect with.

Additionally - security wise - you should disable the root login via ssh (PermitRootLogin no in sshd_config). It's not wise to allow it.

i tried... didnt helped... thanks anyway ".rdg"

maybe someone can post his sshd_config and i will copy it??

---

### Post by .rdg on 2007-04-26
Perhaps I didn't get your first message correct. Could you be more specific as to what are you trying to achieve? Be as specific as you can (you can actually use virtual user name and virtual host for description) so then I can help you out.

Regards,
.rdg

---

### Post by chacham23 on 2007-04-26
Ok...

I try to log to server (=leeware) from my computer with ssh

i try this with this command:
```

root@assaf-desktop:/etc# ssh vps555@leeware.com -l root
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).

```

vps555 - is the server name
leeware.com - is the domain name

i try to log as root
the password i typed is true and i can log with the pass from another computer... the problem is on my computer i also checked with the support of the domain:
"I have verified that I can logon to your machine both locally and remotely."

i also searched on google and i find some solution involved with the file sshd_config  so i think it something in it... or not :)

---

### Post by .rdg on 2007-04-27
First of all - your settings (posted in 1st message) are just fine. The default is to enable logging in with the password, so the hashed line:

#PasswordAuthentication yes

is nothing to be worried about. Also - when you trying to log in you are asked for the password - you wouldn't be if it was explicitly set to no.

Anyway the command you should be runninng IMHO is (doesn't matter if run by local root or no):

ssh -l root vps555.leeware.com

Which is host vps555 in leeware.com domain.

The way you used it is incorrect - it would mean that you are trying to connect to host: leeware.com using both vps555 and root users at the same time (so you should remove one of them).

Anyway - I did a little search for host vps555.leeware.com and it's a non-existent domain name. So probably the vps555 is just a user name, not a hostname (or is it bogus name you shown to keep some data private)?

Connecting to any ssh server in my case wasn't any different with Ubuntu (or any other Linux) than it was with Windows. There's something you are doing wrong (at least seems so).

Regards,
.rdg

---

