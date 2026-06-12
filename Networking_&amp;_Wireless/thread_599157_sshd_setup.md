---
title: "sshd setup"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by justinhj on 2007-11-01
I'm having a hard time getting ssh to work from outside my network. I chose a port and changed the port in the /etc/ssh/sshd-config  file to match. 

I can do ssh localhost, and I can connect from other machines on my network using 

ssh 192.168.0.100

And everything is fine. 

But when I access from outside the network, or from inside using my external IP the connection sits there with no response. 

If I telnet directly to the port and IP I get the following output... (ip address changed)

Connected to 99.99.99.99.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.6p1 Debian-5build1


And then it sits there. 

So I think my port forwarding is working on the network. But I have something not set up right?


Justin

---

### Post by almax00 on 2007-11-01
you are using a router? you have to forward the external (public) port to the internal (private) port via the router. i have an smc router and it is called "virtual private network" under the NAT tab. if you are outside you would use ssh user@99.99.99.998:XX where XX is the external port number.

---

### Post by justinhj on 2007-11-01
Yes the port forwarding is setup to send my desired port to my computer running ubuntu. And I'm pretty sure the port forwarding is correct since I can connect to the port and IP from outside the network using telnet. 

But when I connect with ssh it just hangs there.

---

### Post by jerrybme on 2007-12-10
justinhj :
Any luck resolving this? I just upgraded to Gutsy and now can't connect remotely any more. sshd_config file looks ok and I can connect while on the network. I can ping my box from the internet but no response from the ssh server. Wierd

Here's my sshd config

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

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

ChallengeResponseAuthentication no

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes

AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

