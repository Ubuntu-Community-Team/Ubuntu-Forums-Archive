---
title: "How to Connect to server?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by 007casper on 2011-01-24
I went to Places > Connect to Server

I tried many things for location such as IP, server name etc.  I just cannot connect to the server.  Please advise.  Thank you.
> 
Custom Location

Location (URI) ?

I get
> 
Cannot Connect to Server.  You must enter a name for the server.

Please enter a name and try again.

---

### Post by 007casper on 2011-01-24
however, I can connect through terminal.  Because of this, I should be able to connect through "Places>Connect to Server"

The same URI doesnt work.  I am wondering what is the proper path?

Please, advise.

Thank you so much.

---

### Post by cariboo on 2011-01-24
What commands are you using to try and connect to your server in nautilus, how do you connect via a terminal?

---

### Post by 007casper on 2011-01-24
I tried
name@IP

it didnt work. 

Since it is shared IP.  

I tried servername@IP that didnt work either.

However, I cant load Help menu either.  I wonder if there is something wrong with "Connect to Server"  I get 
> The requested URI "ghelp:user-guide#nautilus-server-connect" is invalid

The only pull down menu I get - Service type: "Custom Location"

so, I wonder if there is something wrong with the application.  I remember years ago, I was able to connect through it before updating ubuntu etc.

I found this link.  However, as I said I dont get options in the pull down menu.
[http://ubuntuforums.org/showthread.php?t=1573186&highlight=Places+Connect+Server](http://ubuntuforums.org/showthread.php?t=1573186&highlight=Places+Connect+Server)

in the terminal, I put 

> ssh [email]name@servername.domain.com[/email]

then it asks for password, and then I am in.

??

thanks

---

### Post by spcwingo on 2011-01-24
I see that you're trying to connect via SSH.  You can do that in "Remote Desktop Viewer" that is installed by default in Ubuntu.  You should lbe able to find it under Applications>Internet>Remote Desktop Viewer.  I know that it works for SSH because that is what I use to login to my server.

---

### Post by 007casper on 2011-01-24
I dont have Applications>Internet>Remote Desktop Viewer on my local server.

the server I am trying to connect doesnt have desktop interface. I am just trying to mount the other server drive through "Connect to Server" (nautilus-server-connect)  However, the only option I get in the pull down is 'custom location' and nothing else.

---

### Post by JC Cheloven on 2011-01-24
> **007casper said:**
> I dont have Applications>Internet>Remote Desktop Viewer on my local server.

the server I am trying to connect doesnt have desktop interface. I am just trying to mount the other server drive through "Connect to Server" (nautilus-server-connect)  However, the only option I get in the pull down is 'custom location' and nothing else.
Then why don't use ```
ssh username@hostname
``` and proceed from there? 
Is it what you did when you "were able to connect from terminal? Or what was it?

---

### Post by spcwingo on 2011-01-24
I just assumed by the commands that you had posted that you were trying to SSH into your server (with no GUI, just like mine).  If you're trying to mount a share over your network I have to ask if you have samba (or NFS, etc) installed and configured.  If not, here's a how-to:

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

---

### Post by cariboo on 2011-01-24
You can connect to the server, using sftp in nautilus, or almost any other file-manager. Open nautilus, press Ctrl-l to get the address bar, then type:

```
sftp://user@server
```

Using sever in the above command only works if you have a server name aliased to an ip address in /etc/hosts, if you haven't done that, use the ip address.

---

### Post by 007casper on 2011-01-24
@JC Cheloven
I used ssh username@servername.domainname.com

and then I am able to ssh to server.

In addition to that I would like to mount the drive through nautilus in order to multitask.

I think there is something wrong nautilus-server-connect, because I dont get pull down menu.  How can reinstall it?  Or is there a specific reason why I am not getting the pulldown menu.

@spcwingo
I dont have samba installed

@cariboo907
Could not display "sftp://user@servername.domain.com/" on nautilus

Nautilus cannot handle "sftp" locations.

---

### Post by 007casper on 2011-01-31
Places > Connect to Server (nautilus-server-connect)

what is the proper way of making it work?

thank you.

---

### Post by 007casper on 2011-02-02
this may be obvious to everyone. However, I really need to use "Connect to Server".

I dont get anything but Custom Location - Location (URI)

what is the proper way of doing this? 

since I am not getting any replys, I am wondering if the answer is there and I am not seeing it.

I dont have samba installed because both machines are linux.  The local machine has ubuntu, and the remote machine has debian.

thx

---

### Post by JRV on 2011-02-02
Try this.

On the server:
```


  sudo apt-get install ethtool openssh-server

```
 
Then you need to modifiy the /etc/ssh/ssh_config file on the clients.

Here is mine:

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
   ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
  PasswordAuthentication yes
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
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


```

And modify the /etc/ssh/sshd_config file on the server.

Here is mine:

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

RSAAuthentication no
PubkeyAuthentication no
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
PasswordAuthentication yes

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

To connect:

```


ssh -X USER@HOSTNAME


```

---

### Post by 007casper on 2011-02-02
the remote server is in shared environment.  I cant access etc on the remote server.  I changed my local ssh_config still no luck.

However, I was able to login before while back without changing ssh_config, I think I was able to choose more than "Service type:Custom Location" in the pull down menu.

I tried many different ways of putting the information. I constantly get
> 
Cannot Connect to Server. You must enter a name for the server.

Please enter a name and try again.

I have been checking everywhere for additional info and cant seem to get my hands on... 

manual page doesnt have much info on this
[http://manpages.ubuntu.com/manpages/hardy/man1/nautilus-connect-server.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/nautilus-connect-server.1.html) 

please let me know how I can access the server.  I figure since I can access it through terminal, I should be able to connect through places>conncet to server - nautilus.  Thank you.

---

### Post by 007casper on 2011-02-11
bump

---

### Post by 007casper on 2011-02-11
I tried on my friends computer and I was able to connect without a problem.  The problem must be nautilus-server-connect on this computer.  I did sudo apt-get nautilus-server-connect and it gave me an error.  I dont see it on the synaptic package manager either, I tried it as "To Access a remote server" or "nautilus-server-connect".  What is the proper name for it?  I would like to reload it so I can use it.  Thank you.

---

### Post by 007casper on 2011-02-15
how come I cant pull down the menu on "connect to server"  I dont get any options.  No ftp, no ssh etc.  The only thing listed is Custom Location, which doesnt work.  I checked the manuals, it doesnt have any documentation on it.  Thank you.

Please advise.

Thank you. I really appreciate it.

---

### Post by 007casper on 2011-02-16
When I Select Places->Connect to server from GNOME desktop, I only get the Custom Location in the drop-down.  And whatever I type it just doesnt work.  I dont get SSH, FTP (login), Public FTP, Windows Share, WebDAV, Secure WebDAV

I found this old link over here [http://ubuntuforums.org/showthread.php?t=1099095](http://ubuntuforums.org/showthread.php?t=1099095), and I also found that people had issues similar to mine with webdav.  I just need SSH to work.  If I can get that in the drop down, that will be awesome.  It will allow me work fast.

Please advise.  Thank you

---

### Post by crymsonfyre on 2012-07-31
Has anyone figured this out? I am unable to see my ssh under connect to server as well. i am unsure of how i deleted these options as of late? Please can someone help me with this. I am able to use terminal, just not the options under connect to server?

> **007casper said:**
> When I Select Places->Connect to server from GNOME desktop, I only get the Custom Location in the drop-down.  And whatever I type it just doesnt work.  I dont get SSH, FTP (login), Public FTP, Windows Share, WebDAV, Secure WebDAV

I found this old link over here [http://ubuntuforums.org/showthread.php?t=1099095](http://ubuntuforums.org/showthread.php?t=1099095), and I also found that people had issues similar to mine with webdav.  I just need SSH to work.  If I can get that in the drop down, that will be awesome.  It will allow me work fast.

Please advise.  Thank you

---

### Post by wildmanne39 on 2012-07-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

