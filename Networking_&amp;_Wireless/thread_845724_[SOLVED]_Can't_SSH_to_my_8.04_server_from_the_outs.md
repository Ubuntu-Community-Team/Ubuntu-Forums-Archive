---
title: "[SOLVED] Can't SSH to my 8.04 server from the outside"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by starfleetcaptainrob on 2008-06-30
I've been trying to figure this out for a few days now, and to me everything looks fine.  I can ssh to my server from within my home network just fine, but when I go to work and try to do it, no dice.  I get a ssh_exchange_identification: Connection closed by remote host.  I've forwarded the 33574 port on my router.  Could it be some permissions issue?

Here's a look at my config file:

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 33574
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
# HostKey for protocol version 1
# HostKey /etc/ssh/ssh_host_key
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
PermitRootLogin no
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

#Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

Hopefully someone has some ideas...

---

### Post by caljohnsmith on 2008-06-30
I'm not a ssh expert, but you might want to at least check that your port is truly open: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by starfleetcaptainrob on 2008-06-30
Good call, but the port is open:

Success: I can see your service on ***.***.***.*** on port (33574)
Your ISP is not blocking port 33574

Nifty tool though, going to have to bookmark that.  Thanks!

Anyone else got any ideas?

---

### Post by superprash2003 on 2008-07-01
do you have firestarter or anything similar installed?

---

### Post by herger on 2008-07-01
Hi all! I have a similar problem.  ](*,)
On my Dell XPS 1330 with _Gutsy_, I have ssh properly functioning (I can connect to every pc in my office).
The vice-versa is impossibile: I cannot access my laptop via ssh from anywhere.
I have NO routers, just direct LAN connection.

I post You some information that may be useful


> $ nmap -p 22 <ip_address>

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-07-01 10:27 CEST
Interesting ports on <ip_address>:
PORT   STATE    SERVICE
22/tcp filtered ssh

Nmap finished: 1 IP address (1 host up) scanned in 10.364 seconds


then


> $ nmap -P0 localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-07-01 10:34 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
538/tcp open  gdomap
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.072 secondswhat can I do?

I have already tried


> $ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 22 -j ACCEPT

but nothing chanced: I need to access my laptop from another pc to back up some large files....

Thanks in advance and regards

Herger

---

### Post by starfleetcaptainrob on 2008-07-01
> **superprash2003 said:**
> do you have firestarter or anything similar installed?

I know Firestarter is not installed.  I installed the server version of 8.04, is there a firewall program that comes standard with that that I am neglecting?

---

### Post by prats84 on 2008-07-01
well i am new to Linux and i had the same issue .

what i did was allowed all host in the file /etc/hosts.allow by adding 
ALL:ALL

first open the file with sudo nano /etc/hosts.allow 
 and then add
  ALL:ALL


I am not sure if would help cause i dont have much knowledge bout Linux.. but it worked for me

Pratik

---

### Post by starfleetcaptainrob on 2008-07-01
> **prats84 said:**
> well i am new to Linux and i had the same issue .

what i did was allowed all host in the file /etc/hosts.allow by adding 
ALL:ALL

first open the file with sudo nano /etc/hosts.allow 
 and then add
  ALL:ALL


I am not sure if would help cause i dont have much knowledge bout Linux.. but it worked for me

Pratik

I believe I told it ssh1 ssh2:all in the hosts.allow file, or something like that.  I will have to try ALL:ALL tonight.  Thanks!

---

### Post by starfleetcaptainrob on 2008-07-01
I tried changing my hosts.allow file as suggested and still cannot get in.  Anyone else have anything?

---

### Post by starfleetcaptainrob on 2008-07-01
Here's the output of netstat -antp

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4312/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      4394/smbd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      4486/perl
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4463/apache2
tcp        0      0 192.168.10.10:53        0.0.0.0:*               LISTEN      4192/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4192/named
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      4192/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      4394/smbd
tcp        0      0 192.168.10.10:445       192.168.10.2:49161      ESTABLISHED 5103/smbd
tcp6       0      0 :::33574                :::*                    LISTEN      5812/sshd
tcp6       0      0 :::53                   :::*                    LISTEN      4192/named
tcp6       0      0 ::1:953                 :::*                    LISTEN      4192/named
tcp6       0      0 192.168.10.10:33574     192.168.10.2:62020      ESTABLISHED 6362/sshd: fredbear

```

And here's the output of iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Maybe those clues could help someone figure this mystery out...:)

---

### Post by starfleetcaptainrob on 2008-07-01
New wrinkle to the mystery.  I'm using VPN to connect back to my work's network and am using PuTTY to connect to a laptop sitting on my desk at work to try and reconnect back to my server here.  I installed nmap to try and see if the port was open and am getting this message:

PORT        STATE   SERVICE 
33574/tcp   closed  unkown

On my router I've got the port forwarding to that address via that port...but if it was closed on the machine how would I be able to get in from computers on my home network??  I'm using DD-WRT on my Motorola router...

---

### Post by dynamethod on 2008-07-01
other thing to take into account is your external IP address, my ISP changes mine from time to time, so i had to register at dyndns and setup a hostname, my router has an inbuild function to update my external IP with my hostname, then i just put my hostname into putty and my port and away i go, if your router has NAT you shouldnt have to worry about port forwarding, otherwise just open up your port, and if your router doesnt have the same functionality as mine then just use:

sudo apt-get install ddclient

configure it to update to your hostname and away you go


also make sure that if your trying to access it from say for instance your workplace, make sure that your using the companys proxy name and port to get out(put that somewhere in the putty settings, thats what i have to do anyway)

and also if you do ssh outside from your workplace might pay to use a port that doesnt look suspicious, i personally use port 443, so when the tech guys see the traffic its encrypted and doesnt look so suspicious(443, SSl)

---

### Post by starfleetcaptainrob on 2008-07-02
> **dynamethod said:**
> other thing to take into account is your external IP address, my ISP changes mine from time to time, so i had to register at dyndns and setup a hostname, my router has an inbuild function to update my external IP with my hostname, then i just put my hostname into putty and my port and away i go, if your router has NAT you shouldnt have to worry about port forwarding, otherwise just open up your port, and if your router doesnt have the same functionality as mine then just use:

sudo apt-get install ddclient

configure it to update to your hostname and away you go


also make sure that if your trying to access it from say for instance your workplace, make sure that your using the companys proxy name and port to get out(put that somewhere in the putty settings, thats what i have to do anyway)

and also if you do ssh outside from your workplace might pay to use a port that doesnt look suspicious, i personally use port 443, so when the tech guys see the traffic its encrypted and doesnt look so suspicious(443, SSl)

I've already got a DYNDNS account set up.  I'm using my router firmware (DDWRT) to keep DYNDNS updated.  I'll give the proxy name a try tomorrow...thanks!

---

### Post by dynamethod on 2008-07-02
Yeah the company proxy will be stopping you from ssh'ing, try open up firefox at work, and go to the networks tab, that will tell you what the proxy url is, copy and paste that into the address bar and it should show you the port details on the page

---

### Post by starfleetcaptainrob on 2008-07-19
Ah, finally figured it out this week (been kind of busy at work and at home, so haven't had much time to play with it.)  What happened was my employer blocks outbound traffic on all ports besides 80, 443, 21, and a few others.  Needless to say my made up port and port 22 were both blocked.  I tried it with port 443 and was able to log in just fine.  Thanks for everyone's help!  :)

---

