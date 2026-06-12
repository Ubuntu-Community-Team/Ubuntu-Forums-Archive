---
title: "Can SSH to Ubuntu from inside the network, but not from outside."
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by crankyoldbugger on 2015-07-07
I have one Ubuntu box that has a strange connection problem..  I cannot connect from outside the network to either SSH (22) or VNC (5900), but I can from inside the network using a direct IP address.  I have other Ubuntu machines in a similar situation that can connect without any issues.  Just this one box that doesn't like the outside world.

Here's the scenario:

I use dyndns to set up FQDNs for my devices.  All Ubuntu devices have ddclient running as a service to keep the dyndns address current.  I also have Port Forwarding set up on my router for each relevant device on the lan.

So if I'm away from home I can SSH or VNC to my Ubuntu machines using the FQDN.  I use unique oddball port numbers from the remote site to specify which device I want to SSH to.  (i.e. let's say I have port forwarding set up so that anything that comes in on port 34567 (as an example) gets forwarded to port 22 on hostname1).

I can SSH to hostname1 using hostname1.dyndns.com -p34567.  You would think that a very similarly configured hostname2 would allow SSH using hostname2.dyndns.com -p 54321.

So, on one of my Ubuntu desktop machines, this all works fine.  However on my laptop, I cannot connect from outside the network (inside the network I can connect fine by using port 22 and the local IP address 10.x.x.x).

So Port Forwarding is set up right.
dyndns is set up right, as is ddclient.
SSH works locally (using port 22 and local IP), so SSHD is set up right.
A similarly configured machine works right, so I'm assuming that the problem is unique to the laptop.
Canyouseeme.org says that port 22 is not blocked.

If I try to connect remotely using PuTTY, I get the errors:

Event Log: We claim version: SSH-2.0-PuTTY_Release_0.64
Event Log: Failed to connect to [ip address removed]: Network error: Connection refused
Event Log: Network error: Connection refused


My wild guess is that something got mis-configured deep in the laptop, but for the life of me I can't think of where else to check.

---

### Post by Plueonic on 2015-07-07
Could you post the relevant parts of your sshd_config and the port forwarding rules? Also see if dyndns is up to date.

The way i usually go about it is configuring ssh to use the specific port I want to and specifying it when connecting from a remote machine.

---

### Post by crankyoldbugger on 2015-07-07
OK, as I mentioned the Port Forwarding the router simply takes anything coming in on port xxxx and forwards it to port 22 on the laptop's local IP.

As to the sshd_config, it's pretty much the factory default:

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
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes


# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024


# Logging
SyslogFacility AUTH
LogLevel INFO


# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes


RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys


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
Banner /etc/issue.net


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


AllowUsers (my user name)

---

### Post by Plueonic on 2015-07-07
Assuming you've set it up to use 9876, you're trying to connect to that port right? This part got me confused a little bit cause you should be checking 9876
> **crankyoldbugger said:**
> 
Canyouseeme.org says that port 22 is not blocked.


Also a little something to add, if both machines are behind the same router, shouldn't you be able to use the same hostname for both the machines since both will have the same records? I'd still suggest double checking your port forwarding rules since you're able to login to the machine from within the network

---

### Post by crankyoldbugger on 2015-07-07
Thanks for replying.  

I've gone over the port forwarding rules several times.  As a matter of fact, I get the same fail whether I aim for the ETH0 or WLAN0 IP address.

Both machines have their own dyndns records, just as an extra layer of separation.

But yes, I'm trying to connect to the correct port (as in your example, 9876).  The router should then forward this on to port 22 to the appropriate IP address.

---

