---
title: "SSH from behind firewall?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by Znupi on 2007-05-03
I have successfully installed ssh on my ubuntu and am able to connect to it, so its set up correct. The problem is that I want to connect to it using putty (or winscp), from school. But at school, they have a firewall (most probably), and it doesn't work (the connection times out). Is there any way to connect to my ssh in linux, from behind a firewall? :|

---

### Post by dbott67 on 2007-05-03
It depends on the setup (theirs and yours).

Are you using any sort of NAT router at home (Linksys, D-Link, Netgear, etc.)?  If so, these are the basic steps for external access:

1. Login to the router and forward port [COLOR=Red]**22**[/COLOR]* to the IP address of your Ubuntu computer.

2. Most home-based NAT routers have support for [Dynamic DNS]("http://www.dyndns.com/services/dns/dyndns/").  Create an account and then you'll be able to SSH via hostname (i.e. Znupi.dyndns.org) rather than IP address.

If your router does not support dynamic DNS, then try one of these apps:
[http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

3. Install & configure open-ssh on your Ubuntu computer to listen on port 22 (the default).  Just installing it from the repos will do this.

4. Attempt to connect from your school using PuTTY.  Use your newly created dynamic DNS hostname as the address.

If you still get blocked, it means that (more than likely) your school blocks port 22. One of the tricks to try to figure out which ports are available is to use telnet to try to access ports and use one of those to forward to your Ubuntu box.

```
dbott@feisty:~$ telnet myaccount.dyndns.com [COLOR=Red]22[/COLOR]
Trying 69.49.xxx.yyy...
Connected to myaccount.dyndns.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
```Replace the 22 with whatever port you've forwarded on your router.  For example, suppose your school permits port 80.  You could forward port 80 on your router to port 22 on your Ubuntu box (as long as you weren't already forwarding port 80).  Personally, I use port an arbitrary high numbered port (like 9922) to forward to port 22.

If your setup is different, please provide info on how your computer is connected to the internet (DSL/cable, router or direct connection, firewalls, etc.).

-Dave

---

### Post by dannyboy79 on 2007-05-03
well how fast does it timeout? my connection times out as well. that the way the server is setup by default. BUT if you're doing stuff and the connection times out, than yeah, something is wrong. you'll need to look at the log files on your ssh server to see what is occuring. u can view /var/log/auth.log

so that would be done with this

sudo gedit (or fav text editor) /var/log/auth.log

and you'll see something like this in it: 

May  3 12:45:33 ubuntu sshd[18827]: Accepted publickey for XXXXXXXX from XX.XXX.XX.XXX port XXXXX ssh2

obviously the X's are numbers and letters that I don't want anyone to know.
and this is telling you what IP address is connecting to your server and thru what port on their end. then a little lower should be the reason it's closing.

i am pretty sure the default server has nothing that will disconnect you automatically so I know that my company's firewall is dropping my connection when I am not doing anything for awhile but that's after like an hour or so. i am not sure how to make it seem like you're working all the time.

well again,  you need to clarify whether or not you're getting booted immediately or what?

---

### Post by Znupi on 2007-05-03
No I don't have a router (though it's possible to get one soon, so thanks for the info!).
I have installed open-ssh and it works, I'm sure about it, I've tested it from a friend.
I will try to portscan my school's PCs and see which ports are open, but how do I change the port ssh listens to? So I can connect with putty to my PC on port [whatever].

I'm connected directly to the internet, with a DSL cable. That's basically all.

---

### Post by dbott67 on 2007-05-03
> **Znupi said:**
> ...how do I change the port ssh listens to? So I can connect with putty to my PC on port [whatever].

I'm connected directly to the internet, with a DSL cable. That's basically all.

```
dbott@feisty:~$ sudo gedit /etc/ssh/sshd_config 
# Package generated configuration file
# See the sshd(8) manpage for details

[COLOR=Red]# What ports, IPs and protocols we listen for
Port 22[/COLOR]
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

```

Change "[COLOR=Red]Port 22[/COLOR]" to whatever you want.

-Dave

---

### Post by Znupi on 2007-05-10
Thanks, it worked for port 8080 :).

---

### Post by dbott67 on 2007-05-10
Glad to hear it.

---

