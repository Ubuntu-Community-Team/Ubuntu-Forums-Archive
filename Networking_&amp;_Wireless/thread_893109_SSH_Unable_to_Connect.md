---
title: "SSH Unable to Connect"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by G-mL on 2008-08-17
I need to configure SSH to work on my computer because I need to log into it from school (Windows).

Here's the deal.

This is what I'm getting:
```

$ ssh -vvv ajay-laptop.no-ip.org
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ajay-laptop.no-ip.org [72.79.126.4] port 22322.

```

Then it stops and times out.

As you can see, I'm using no-ip.org for my dynamic ip address and have changed the default port to 22322. I have a Belkin router and have port forwarded 22322 to my computer. 

I used Firestarter but uninstalled (and purged) - but it did show me that when I tried to ssh, there were no visible incoming connections - basically showing that it was dropped before it ever got to my computer.

ssh localhost works.

One more thing: I have Verizon as my ISP. Don't know if this matters.

I have checked out other threads on this forum and tried the solutions suggested but none have worked so far. Can anyone point me in the right direction?

Thank you in advance.

---

### Post by tamoneya on 2008-08-17
I had a similar issue when i was trying to setup the same thing.  I had changed my port and after changing it from 22 to 222 it stopped working.  It turns out that my ISP (comcast) blocks most ports with 22 being one of the exceptions.  Try changing it back to the default and see if it solves things.

---

### Post by G-mL on 2008-08-17
I forwarded both 22 and 22322 on my router, so just using the -p should do it right? 

Well, that's what I did. Here are the results (same as before):

```

$ ssh -vvv -p 22 ajay-laptop.no-ip.org
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ajay-laptop.no-ip.org [72.79.126.4] port 22.

```

Should I change it in /etc/ssh/ssh_config and sshd_config also?

---

### Post by tamoneya on 2008-08-17
yes you should change the config file and then restart sshd

---

### Post by G-mL on 2008-08-17
Okay, did that; no change. Results are posted below:

```

ajay@ajay-laptop:~$ sudo vim /etc/ssh/sshd_config
ajay@ajay-laptop:~$ sudo vim /etc/ssh/ssh_config
ajay@ajay-laptop:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                                                                                                        [ OK ] 
ajay@ajay-laptop:~$ ssh -vvv ajay-laptop.no-ip.org
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ajay-laptop.no-ip.org [72.79.126.4] port 22.

```

Sorry, this is really not working...

---

### Post by Yuki_Nagato on 2008-08-17
Can you try:

[email]XXX@ajay-laptop.no-ip.org[/email] (XXX is the intended login name)

instead of plain old 

ajay-laptop.no-ip.org.

---

### Post by G-mL on 2008-08-17
Same results.

```

ajay@ajay-laptop:~$ ssh -vvv ajay@ajay-laptop.no-ip.org
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ajay-laptop.no-ip.org [72.79.126.4] port 22.

```

Should I post my /etc/ssh/ssh_config and sshd_config files for reference?

---

### Post by tamoneya on 2008-08-17
> **G-mL said:**
> Same results.

```

ajay@ajay-laptop:~$ ssh -vvv ajay@ajay-laptop.no-ip.org
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ajay-laptop.no-ip.org [72.79.126.4] port 22.

```

Should I post my /etc/ssh/ssh_config and sshd_config files for reference?

It couldnt hurt to post but I dont think we will find anything of interest in there.  how are you changing these files if you are not internally connected?

---

### Post by Yuki_Nagato on 2008-08-17
I do not believe that would pose a security issue.  Please post your config files.

---

### Post by G-mL on 2008-08-17
> **tamoneya said:**
> It couldnt hurt to post but I dont think we will find anything of interest in there.  how are you changing these files if you are not internally connected?

Actually, as you can see from "ajay@ajay-laptop:~$", I'm on the computer that I'm trying to ssh into. For now, I'm only testing it out (also tried with PuTTY on an XP box; same results). This shouldn't matter though, right?

I have attached the files below for your convenience:

```


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
   ForwardAgent no
   ForwardX11 no
   ForwardX11Trusted yes
   RhostsRSAAuthentication no
   RSAAuthentication yes
   PasswordAuthentication yes
   HostbasedAuthentication no
   GSSAPIAuthentication no
   GSSAPIDelegateCredentials no
   GSSAPIKeyExchange no
   GSSAPITrustDNS no
   BatchMode no
   CheckHostIP yes
   AddressFamily any
   ConnectTimeout 0
   StrictHostKeyChecking ask
   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/id_rsa
   IdentityFile ~/.ssh/id_dsa
   Port 22
   Protocol 2,1
   Cipher blowfish
 #  Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
 #  MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
   EscapeChar ~
 #  Tunnel no
 #  TunnelDevice any:any
 #  PermitLocalCommand no
 #   SendEnv LANG LC_*
 #   HashKnownHosts yes
 #   GSSAPIAuthentication yes
 #   GSSAPIDelegateCredentials no

```

And the sshd_config:

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
ListenAddress *
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
PermitEmptyPasswords yes

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

AllowUsers *

```

I might have fudged some things up here... please let me know if I did so. 

Thank you very much for your quick responses.

---

### Post by G-mL on 2008-08-18
Hey guys, I asked a friend for his /etc/ssh/ssh_config file to compare and changed my settings to match his. Here is my now updated ssh_config file:

```


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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

Thanks.

---

### Post by tamoneya on 2008-08-18
i took a look at your ports and i noticed that port 22 is filtered.  ```
PORT     STATE    SERVICE
22/tcp   filtered ssh
80/tcp   filtered http
88/tcp   filtered kerberos-sec
135/tcp  filtered msrpc
136/tcp  filtered profile
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
443/tcp  filtered https
445/tcp  filtered microsoft-ds
515/tcp  open     printer
5900/tcp open     vnc

```
Is there some sort of filter in your firewall or something?

---

### Post by G-mL on 2008-08-18
Hm, I don't believe that I have any filters on my firewalls. How would I go about checking that?

Update: Also, I used [this website](http://www.serfish.com/console) to try to SSH from the internet (since it wasn't working from my laptop) and it got up to the point of RSA Authentication but then, I get the following error message:

```

Permission denied, please try again.

``` 

This happens regardless of what I enter. It just does not recognize my password. 

Any suggestions?

---

### Post by G-mL on 2008-08-18
I have another update:

I remade my RSA keys using ssh-keygen -t rsa and then a friend was able to ssh into my computer without a problem. However, I am still not able to ssh into my own computer. Does anyone have any suggestions as to why this is the case?

---

### Post by G-mL on 2008-08-19
*Bump*

Does anyone know why I am unable to connect to my computer from my computer, but am able to do so from a friend's computer (who runs Ubuntu as well)?

---

### Post by gradinaruvasile on 2009-11-13
Try renaming your ~/.ssh/known_hosts file.

---

### Post by YarDYar on 2009-11-24
This is the first google result for searching " ssh_connect: needpriv 0". 
Can you give us an update of what happened, G-mL?

Fanks,
Yar

---

### Post by xxthegonzxx on 2011-09-20
Can you please give us an update of what eventually happened. This is one of the first results for google. I'm having similar issues and I'm pretty sure it's a firewall issue. Please get back to us. Thanks!

---

