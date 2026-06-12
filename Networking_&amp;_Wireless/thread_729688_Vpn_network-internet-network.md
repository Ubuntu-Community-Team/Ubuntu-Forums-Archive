---
title: "Vpn network-internet-network"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by georgyous on 2008-03-20
I need some help with a VPN.....I tried openvpn and swan and can't get them to work. My problem looks like this 
network1 with eth0 86.124.X.X eth1 10.0.50.1 
network2 with eth0 86.124.X.X eth1 10.0.20.1

the networks are using nat to get to the internet.
bouth have same provider and ping of 1ms on the other side.

I need bouth internal networks to see each other like they are in the same lan. 
can somebody please felp me with a walkthrow something tested by them....because I am trying for a week and can't get it to work.
thank you. a good day to you all

---

### Post by dmizer on 2008-03-20
try this: [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

---

### Post by georgyous on 2008-03-20
it doesn't want to create a tunnel......gives a damn error

ifconfig tun0 10.0.0.100 pointopoint 10.0.0.200
SIOCSIFADDR: No such device
tun0: ERROR while getting interface flags: No such device
SIOCSIFDSTADDR: No such device
tun0: ERROR while getting interface flags: No such device

I found that before I posted here:)

---

### Post by dmizer on 2008-03-20
post the contents of /etc/ssh/sshd_config from the computer you are trying to connect to

your ssh command should look something like this:
```
ssh -w 0:0 serverip
```
where "serverip" is the WAN ip of the computer you are trying to connect to.

---

### Post by georgyous on 2008-03-21
I don't want want this connection just for ssh I want it for all trafic between my internal network and the other internat network........for games and other kinds of traffic

---

### Post by georgyous on 2008-03-21
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

---

### Post by georgyous on 2008-03-21
that is what is inside that config file

---

### Post by dmizer on 2008-03-21
not sure what you mean by "just for ssh".  ssh is a very powerful tool which allows you to perform a host of activities on remote computers, including (but not limited to): opening remote gui applications locally, tunneling remote desktop access, share files, encrypt insecure file protocols like FTP, and much more. in otherwords, ssh is as good as if you were physically sitting at your remote computer.

in this case, ssh is the method by which you can establish a vpn connection, rather than trying to configure something like openvpn. so via ssh, your remote computer and your local computer will appear as though they are on the same network.

so i see in your config file, that you have not added the all important:
```
PermitTunnel yes
```
option which will allow a vpn tunnel to be created via ssh.  so, add this option, restart ssh and run through the tutorial again.

---

