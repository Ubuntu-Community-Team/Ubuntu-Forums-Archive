---
title: "ssh log in problems"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-04-05
i can log in as root but cant log in as admin user it will ask for a password but always denies it but it will work as root no prob and i have been through every inch of this darn comp need help i dont want to remot in as root with only one screen i cant monitor the traffic i dont feel safe can some one help me O i used to be able to log in just fine dont know what happen it has been about a month since i was able to use ssh as a admin user

---

### Post by Eiríkr on 2008-04-05
If at all possible, please use more punctuation in future posts.  Your post here is quite difficult to read.  :-|

Have a look at the various files in the /etc/ssh directory, in particular the ssh_config and sshd_config files.  I'm not familiar with the options used in these files, but looking over the man pages for each, I wonder if perhaps you have something set for the DenyUsers option in the sshd_config file?

HTH,

Eiríkr

---

### Post by kevdog on 2008-04-05
I dont think you can ssh as root, as ubuntu doesnt technically have a root account.

---

### Post by Eiríkr on 2008-04-06
The root account *exists* on Ubuntu (I think it exists on all Unixy systems), but in a default install, the password hasn't been configured and the account might be disabled for logon purposes.  It's plenty possible to change this, though, by just running:
```
sudo su
```
and then altering the root password.  

Cheers,

Eiríkr

---

### Post by Red-Shield on 2008-04-06
i can ssh in as root all i want.  i just cant seem to ssh in, in my admin user name something is really wrong here i am pretty good with ubuntu i am running ubuntu ultimate 7.10 64 bit AMD. look at the print out i need help.

serial-killer@AMD64:~$ ssh root@192.168.1.101
ssh_exchange_identification: Connection closed by remote host
serial-killer@AMD64:~$ ssh [email]root@64.13.121.xxx[/email]
[email]root@64.13.121.xxx[/email]'s password: 
Last login: Sat Apr  5 10:29:29 2008 from 192.168.1.1
Linux AMD64 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
root@AMD64:~# exit
logout
Connection to 64.13.121.xxx closed.
serial-killer@AMD64:~$ ssh [email]red-shield@64.13.121.xxx[/email]
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied, please try again.
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied, please try again.
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied (publickey,password).
serial-killer@AMD64:~$ ssh red-shield@192.168.1.101
ssh_exchange_identification: Connection closed by remote host
serial-killer@AMD64:~$ ssh [email]red-shield@64.13.121.xxx[/email]
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied, please try again.
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied, please try again.
[email]red-shield@64.13.121.xxx[/email]'s password: 
Permission denied (publickey,password).
serial-killer@AMD64:~$

---

### Post by Eiríkr on 2008-04-06
It certainly sounds like your ssh config has gotten borked somehow.  If you don't mind fully ripping it out (and losing any configuration changes you may have made in the process), one option would be to fully uninstall and remove the ssh package, make sure the files in /etc/ssh have been deleted, and then reinstall.  

Cheers,

Eiríkr

---

### Post by Red-Shield on 2008-04-06
i tried that it only seems logical that it would work but no it did not fix the problem unless there is a file i missed i was thinking there was a directory some where that had a permission problem i am going to melt this computer soon.

---

### Post by Red-Shield on 2008-04-06
here is the ssh_config file and the sshd_config file see any problems here any one.

red-shield@FederalReserve:~$ cd /etc/ssh
red-shield@FederalReserve:/etc/ssh$ ls
moduli      sshd_config       ssh_host_dsa_key.pub  ssh_host_rsa_key.pub
ssh_config  ssh_host_dsa_key  ssh_host_rsa_key
red-shield@FederalReserve:/etc/ssh$ more ssh_config

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes2
56-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


red-shield@FederalReserve:/etc/ssh$ more sshd_config
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

---

### Post by Red-Shield on 2008-04-06
dose any one know what         #use login no       means this is in the /etc/ssh/sshd_config directory???????

---

### Post by jetsam on 2008-04-06
The man page isn't entirely clear to me.  I think it's used to tell ssh to use an older form of terminal login instead of something newer.  It's commented out in your config file, and commented out in mine as well.  I don't have your problem, so I don't think that's the cause.  

A possibility worth checking-- I came across this in the sshd man page:
> LOGIN PROCESS
     When a user successfully logs in, sshd does the following:

           1.   If the login is on a tty, and no command has been specified,
                prints last login time and /etc/motd (unless prevented in the
                configuration file or by ~/.hushlogin; see the FILES section).

           2.   If the login is on a tty, records login time.

           3.   Checks /etc/nologin; if it exists, prints contents and quits
                (unless root).

          ...

See if you have an /etc/nologin file.  Maybe it's something the ultimate ubuntu maintainers put in because they prefer key based authentication.

---

### Post by jetsam on 2008-04-06
I was probably off base above.  You wouldn't be able to log into the machine in any way as a non-root user if you had an /etc/nologin file.  

Your config files are identical to the defaults, though, so they should be fine.  They work for me at any rate.  

You might get some information by failing to log in, and then going to the server machine and doing:
```
tail /var/log/auth.log
```

You can also get the ssh client to give you a lot of debugging output by running it with the -v option.  One -v gives a lot of output, but you can use two or three to make it more and more verbose.

---

