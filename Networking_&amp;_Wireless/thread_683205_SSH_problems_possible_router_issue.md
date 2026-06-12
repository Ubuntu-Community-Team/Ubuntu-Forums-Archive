---
title: "SSH problems: possible router issue?"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by imaclean on 2008-01-30
Hi,
I need a bit of help to solve a problem with ssh...  I've searched for answers online in this forum & others however I havent been able to correctly diagnose the problem - apologies if this is a dual post...
Basically I am having problems ssh-ing on to my box from an external address.  I can do it localy, I have set up port forwarding (confirmed with [www.canyouseeme.org](www.canyouseeme.org)) and I cant see any problems in the router logs or the servers logs...  
If I run tcpdump -vvvns0, I can see:

23:06:40.168635 00:1d:60:64:71:db > 00:1b:11:e0:f9:38, ethertype IPv4 (0x0800), length 74: (tos 0x0, ttl 64, id 17170, offset 0, flags [DF], proto TCP (6), length 60) 192.168.1.2.58057 > 86.139.51.219.675: S, cksum 0x0e10 (correct), 2624474024:2624474024(0) win 5840 <mss 1460,sackOK,timestamp 13764794 0,nop,wscale 7>
... etc

If I run sshd in debug mode, apart from binding it doesnt log anything so it basically looks like the router firewall is blocking the return however I have moved the server to the DMZ and I still get the same results.
Internally I can telnet to the host/port, externally as expected it hangs...  I've tried an alternative router (a belkin versus a dlink) and I've tried to move it to the DMZ which out any joy.  As far as the server is concerned, both the hosts.allow & hosts.deny are empty and I have not changed/configured any other setting (e.g.  from a pure ubuntu install.  I doubt it matters but my isp is BT internet...
I've run a traceroute:

> traceroute -p 675  86.143.6.65
traceroute to 86.143.6.65 (86.143.6.65), 30 hops max, 40 byte packets
 1  host86-143-6-65.range86-143.btcentralplus.com (86.143.6.65)  1.795 ms  2.229 ms  2.705 ms

A netstat:

netstat -plat
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:ipp           *:*                     LISTEN     -                   
tcp        0      0 localhost:43994         localhost:675           ESTABLISHED7097/ssh            
tcp6       0      0 *:675                   *:*                     LISTEN     -                   
tcp6       0      0 localhost:675           localhost:43994         ESTABLISHED-   

My config is set up as:

########################################################

# What ports, IPs and protocols we listen for
Port 675
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

########################################################
I havent edited the iptables:
> iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I've tried directly from the server, from a windows xp pc on the network, a work linux server & a work xp pc..
I've pretty much checked/uncheked every option available in the router, flashed it, restore it to factory setting etc etc and no joy....
If anyone has any ideas how I can diagnose or fix this issue I would be really grateful...  I basically need to resolve this issue in the next day or two before I leave the country for six months!!!
Many thanks in advance
Iain

---

### Post by imaclean on 2008-01-30
Sorry also meant to mention that moved the port from 22 to 675 to check that the routers own internal ssh server wasn causing problems...
Iain

---

### Post by jetsam on 2008-01-31
You might want to try getting ssh to listen to a normal ip4 socket instead of an ipV6 socket.  
You can do this by removing the # to uncomment the line:
```
#ListenAddress 0.0.0.0
```
from your etc/sshd_config file and then restart sshd like so:
```
sudo /etc/init.d/ssh restart
```
I'm not sure if this will fix your problem.  My set-up actually routes fine through a soho router even though ssh listens on an ipV6 socket.  There's some kind of kernal magic that wraps and unwraps ip4 addresses.  It does seem like it _could_ be a cause of trouble with some routers, and I can't see anything else obviously wrong in what you've posted.

---

### Post by imaclean on 2008-01-31
Thanks for the help!
I've tried uncommenting that line and restarting but still doesnt work...  Is there any way to log if the dlink router is receiving the traffic?  Wondering if its actually my BT thats causing the problems?  Does anyone else have problems with BT?
Does anyone else use the dlink DKT-710 wireless ADSL router?
Iain

---

### Post by jetsam on 2008-01-31
The dlink site for the dkt-710 links to the manual for the dsl-2640b.  Assuming this is just a re-branding and I'm looking at the right manual, you should be able to make the router logs more verbose by going to the router admin interface and setting Maintenance-->System Log-->Log Level to "debugging."  Maybe that will help you figure out what is going on.  

One thing I noticed on thier support page is this question from the faq:
> FAQs for DKT-710
 
Question:
Why can I not access my webserver using the WAN IP address?

Answer:
Your router has no support for NAT Loopback, and can therefore not view a server by its WAN IP, from the LAN.

To view your servers from a LAN computer, use the LAN IP address of the server.

To view your servers from the internet, use the WAN IP address.


That's inconvenient.  You can't really test your set-up using your external ip address from within your own network.

---

