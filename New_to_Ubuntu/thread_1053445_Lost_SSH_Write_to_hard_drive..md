---
title: "Lost SSH Write to hard drive."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Devastator9 on 2009-01-28
I have a SSH server setup and all was working until Kernel updated to 11 from 9.
I have read and write to the server from windoze XP with samba but only read from the other Ubuntu machines using ssh. I could read and write before update 
What steps do I need to take to fix this, remember first time in using ssh server.

---

### Post by yeats on 2009-01-28
Perhaps your upgrade required you to generate new ssh keys?  Is there any error message that happens?  You can find the log information by opening a terminal and doing

```

cd /var/log
grep ssh *

```

or you can browse the authentication log (still in /var/log)

```
less auth.log
```

perhaps you'll find clues there?

feel free to post what you find if it doesn't make sense to you.

---

### Post by Devastator9 on 2009-01-28
What should i like for?
I see alot about Gnome-keyring Demon.

---

### Post by Devastator9 on 2009-01-29
I did an un-install of ssh and then re-installed and setup just like I had it. I ssh into the server see all the files and can copy from server.I just can't create folder are copy to it.
Took me about 12 hours the first time to get it to work learned a lot need to learn more. I did notice that after the kernal to 11 that the sshd_config file is very differnt.
Here is the config have look, I have to be missing something.
In Windoze there is no problem with making folders.


server@anvel-server:~$ cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
ListenAddress ::22
ListenAddress 0.0.0.0
Protocol 2 1
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
HostbasedAuthentication yes
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
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

---

### Post by Devastator9 on 2009-02-15
I got it fixed had ssh setup worng on the client side. Crazy me.

---

### Post by Xiong Chiamiov on 2009-02-15
> **Devastator9 said:**
> I got it fixed had ssh setup worng on the client side. Crazy me.
You can mark a thread as solved using the red "Thread Tools" link in the upper-right of this page.

---

