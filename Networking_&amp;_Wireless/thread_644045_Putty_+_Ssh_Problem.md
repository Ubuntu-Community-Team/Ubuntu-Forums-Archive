---
title: "Putty + Ssh Problem"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by chertour on 2007-12-18
Hi  all , and many thanks for any answers

For a couple of days I try to connect from work (windows xp home)  to home (ubuntu 7.04 out of box 
more or less!!!)  using  putty. The problem is the message 
"Network Error : Connection Timed out"  with all its meaning. 
I have done the following :
1. Port forwarded correctly the 22 port on router to the local machine and checked the sshd_config for correctness (22 port as well).
2. Verified with netstat -pat that service is running.
3. Disabled the firewall initially with firestarter.
3. Connected from the linux box to itself successfully using the DynDns name entry (not the IP)  i.e. ssh [email]root@xxxxxx.dyndns.org[/email] from both the command line and from PUTTY for Linux that I have installed. 
4. For testing purposes I have configured the vnc server on ubuntu and I can connect successfully 
form windows xp (from which I assume that firestarter , port forwarding works and I can configure them).
5. When I try to connect from xp to ubuntu with putty (version 0.60 latest) no luck and after a while 
the message appears. The /var/log/ messages or /var/log/auth does not have any entry (maybe a problem of my configuration).



Do you have any ideas?

Many thanks 

Netstat -pat 

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:2208          *:*                     LISTEN     5229/hpiod          
tcp        0      0 *:nfs                   *:*                     LISTEN     -                   
tcp        0      0 *:645                   *:*                     LISTEN     5554/rpc.mountd     
tcp        0      0 *:45897                 *:*                     LISTEN     5744/rpc.statd      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     5589/smbd           
tcp        0      0 *:vnc                   *:*                     LISTEN     5677/xinetd         
tcp        0      0 *:sunrpc                *:*                     LISTEN     4366/portmap        
tcp        0      0 *:www                   *:*                     LISTEN     5948/apache2        
tcp        0      0 *:x11-1                 *:*                     LISTEN     7660/Xvnc           
tcp        0      0 *:58001                 *:*                     LISTEN     -                   
tcp        0      0 *:ipp                   *:*                     LISTEN     5200/cupsd          
tcp        0      0 localhost:smtp          *:*                     LISTEN     5460/exim4          
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     5589/smbd           
tcp        0      0 localhost:2207          *:*                     LISTEN     5232/python         
tcp6       0      0 *:x11-1                 *:*                     LISTEN     7660/Xvnc           
tcp6       0      0 *:ssh                   *:*                     LISTEN     11534/sshd          
tcp6       0      0 *:ipp                   *:*                     LISTEN     5200/cupsd          

SSHD 

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

---

### Post by csat on 2007-12-18
Try install to your XP a software called freenx client and at your Ubuntu Linux, freeNX client, freeNX node and freeNX server so that it will give you connections. FreeNX is a product of NoMachine.

Another possibility for FTP and Telnet connection from your XP is the use of a software called tunnelier, which is also freeware.

From Ubuntu to your XP you might install SAMBA.  There is a nice tutorial on how to do it here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

With SAMBA installed you can manage folders at both side and printer.

Hope you enjoy those stuff.

---

### Post by trobbins on 2007-12-18
Well, regarding getting ssh working, here are three ideas:

Ok, so you know your SSH server is listening on your Ubuntu box on your home lan behind a router.  You know you can ssh into it from itself.  Do you have other PCs on your lan (behind your router/firewall) that you can use to ssh into the Ubuntu box?  This will prove that your Ubuntu box will accept connections from other IPs besides itself.

On the public side of the router/firewall, can you telnet into port 22?  Do you get anything at all?  Even a blinking cursor? 


Finally, I'm not a networking guru, but do you see the difference between these two lines?

tcp 0 0 *:vnc *:* LISTEN 5677/xinetd
tcp6 0 0 *:ssh *:* LISTEN 11534/sshd

I don't think your ssh server is listening using IPV4.  I'm not sure how it works, but maybe you should find out if you can configure sshd to listen using IPV4?

In Putty, I selected to use an auto configuration rather than explicitly stating I wanted to use IPV4.  This caused all sorts of connection refused messages until I figured I had to change my Putty settings.  This leads me to believe this option is configurable on the server as well.  Good luck.

---

### Post by trobbins on 2007-12-18
Eh, I felt like looking it up.  Here is how you enable IPV4 on your ssh server:

You need to uncomment a line in  /etc/ssh/sshd_config.

partial contents of /etc/ssh/sshd_config:

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0   #<<<---------uncomment this line


Restart ssh server with :

sudo /etc/init.d/ssh restart

SSH should accept IPV4 connections now.

---

### Post by chertour on 2007-12-19
Hi again  , 

Many thanks for the answers.
No success thus far after doing the following:

1. Comment out the line about IPV4 protocol which now is indeed like 
tcp        0      0 *:50503                 *:*                     LISTEN     -                   
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     5845/smbd           
tcp        0      0 *:vnc                   *:*                     LISTEN     5934/xinetd         
tcp        0      0 *:sunrpc                *:*                     LISTEN     4361/portmap        
tcp        0      0 *:www                   *:*                     LISTEN     6149/apache2        
tcp        0      0 *:ssh                   *:*                     LISTEN     8088/sshd  

2. Putty works fine (same version and configuration) form within the LAN either by connecting
directly to the IP or by using xxxxxxx.dyndns.org of the Ubuntu Server but no luck when I connect 
with a modem to some other provider and trying  putty to connect to ubuntu.

3. telnet to port 22 succeeds  from inside the LAN (both with dyndns and with IP only)  but fails from outside. 

From inside lan i have 

dinos@quest:~$ telnet xxxxxx.dyndns.org 22
Trying xx.xx.4.211...
Connected to xxxxxxx.dyndns.org.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

from outside nothing

If you have any more ideas please share.
Many thanks again for the tips

---

### Post by trobbins on 2007-12-19
If telnet/SSH connection fails from outside your LAN, you now know that your router is failing to forward TCP port 22 traffic to your Ubuntu box.  Does your router have an SSH server?  Many do and they listen on port 22.  Try changing the SSH port on your Ubuntu box and forward that new port instead.  If that works, then examine your router closely for an SSH server, find it, and turn it off.

---

### Post by chertour on 2007-12-19
Hi again and many thanks .

Let me update and declare the problem solved.
Many thanks trobbins for pointing a way. To be totally honest yesterday I changed the port 
from 22 to 222 but I had no luck again. I can not fully understand why 
from the host itself  i can use dyndns but from outside I can't. And I can't understand 
because I assume (and please correct me ) that when I do ssh xxxxx.dyndns.org  
traffic is routed to dyndns.org and then it is coming back to local lan again. Effectively

192.168.2.2 ->router -> internet -> router -> 192.168.2.2 . So I consider that the forwarding was correct because internet traffic is routed correctly to port 22 on ubuntu. And why internet traffic is forwarded in one case and not in the other (from the dial - up connection + putty)  
But after trobbins recommendation i decided to do two things . 
1. Boot from xubuntu live cd to have an completely out of box distro.
2. Use port above 1024.

Now I can ssh with putty from any machine but only from ports 1025 and up.
I dont thing that router has an ssh server inside but who knows!!! (router 1540 WG Sagem from Greek Otenet provider) 

Many thanks again and please in case you know write a line to allow me understand
why in one case forwarding works  (for traffic from the machine itself) and in the other
case is not.

---

### Post by daflame on 2007-12-19
> **chertour said:**
> Hi again and many thanks .

Let me update and declare the problem solved.
Many thanks trobbins for pointing a way. To be totally honest yesterday I changed the port 
from 22 to 222 but I had no luck again. I can not fully understand why 
from the host itself  i can use dyndns but from outside I can't. And I can't understand 
because I assume (and please correct me ) that when I do ssh xxxxx.dyndns.org  
traffic is routed to dyndns.org and then it is coming back to local lan again. Effectively

192.168.2.2 ->router -> internet -> router -> 192.168.2.2 . So I consider that the forwarding was correct because internet traffic is routed correctly to port 22 on ubuntu. And why internet traffic is forwarded in one case and not in the other (from the dial - up connection + putty)  
But after trobbins recommendation i decided to do two things . 
1. Boot from xubuntu live cd to have an completely out of box distro.
2. Use port above 1024.

Now I can ssh with putty from any machine but only from ports 1025 and up.
I dont thing that router has an ssh server inside but who knows!!! (router 1540 WG Sagem from Greek Otenet provider) 

Many thanks again and please in case you know write a line to allow me understand
why in one case forwarding works  (for traffic from the machine itself) and in the other
case is not.

I would venture to guess either your provider or the router is blocking ports under 1024 (Maybe to prevent people from offering web servers on their wire).  If you have access to check your router's firewall rules you may find this to be true.

---

### Post by trobbins on 2007-12-19
You still have two major differences between your tests.

When you connect from your Ubuntu box to itself with dyndns name, your data never leaves your network.  The DNS lookup does in order to get the IP of your router, but that is all.  The only thing I can think of is that all ports below 1024 are blocked by your isp?  Well, that's all I have on this one, take care, trobbins.

---

### Post by daflame on 2007-12-19
> **trobbins said:**
> You still have two major differences between your tests.

When you connect from your Ubuntu box to itself with dyndns name, your data never leaves your network.  The DNS lookup does in order to get the IP of your router, but that is all.  The only thing I can think of is that all ports below 1024 are blocked by your isp?  Well, that's all I have on this one, take care, trobbins.

Might want to read through before you post.  Check the post above yours.

---

