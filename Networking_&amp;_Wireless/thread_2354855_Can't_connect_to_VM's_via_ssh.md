---
title: "Can't connect to VM's via ssh"
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by kleanuria on 2017-03-07
I can't connect to my VM's via ssh for some reason.
The VM's have internet. They can use ssh to connect to other computers and so on. Just can't access the VM from my Windows computer.
Port 22 is open on ubuntu. Ssh server is installed, I haven't changed any of the configurations.
It must be on my windows side settings. Any ideas?

---

### Post by ajgreeny on 2017-03-07
Are you using a bridged or NAT network connection in the VMs?
Are you connecting using the hostname or IP?
Are you using password or key authorisation to connect?
Show us the output of ```
cat /etc/ssh/sshd_config
```which may give us some clues, though I admit to no knowledge of connecting to a Linux machine using Windows as I have only Linux machines.

---

### Post by HermanAB on 2017-03-07
Enable verbose error messages to see what is going on with -vvv:

$ ssh -vvv user@server

---

### Post by SeijiSensei on 2017-03-07
The most likely reason is that you're using "network address translation" (NAT) rather than bridged networking.  With bridged networking, the VMs are exposed to the host's network and get addresses there.  With NAT, the VM is hidden behind the host on an entirely separate pair of IP addresses.  In that case you need to use some method of TCP proxying to transport external requests back to the VM's SSH port.  Switching to bridged networking will solve this.

---

### Post by kleanuria on 2017-03-07
The output of sshd_config is following:

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

AllowUsers user

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

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

I have NAT and bridged connection both set and I've tried it on both VirtualBox and VMware.
I have used IP to try and connect not hostname.
I use password.

I can ssh out. I can not ssh in if that makes sense. So if I'm in my virtual machine be it no matter which one. I can go ssh user@172.23.13.15 and successfully connect to it. But if I try connecting to my VM from another computer then they can not get in. Hope that makes sense.

---

### Post by SeijiSensei on 2017-03-07
What IP address does the virtual machine have in bridged mode?

---

### Post by kleanuria on 2017-03-08
ifconfig -a output is this

```
ens33     Link encap:Ethernet  HWaddr 00:0c:29:8d:0c:83  
          inet addr:192.168.25.178  Bcast:192.168.31.255  Mask:255.255.248.0
          inet6 addr: fe80::1524:994b:4d68:2364/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13557 (13.5 KB)  TX bytes:6697 (6.6 KB)

ens38     Link encap:Ethernet  HWaddr 00:0c:29:8d:0c:8d  
          inet addr:192.168.200.132  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::136:da8:1790:ba7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6284916 (6.2 MB)  TX bytes:159844 (159.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:45909 (45.9 KB)  TX bytes:45909 (45.9 KB)


```

I got the problem fixed.
Just to recap:
   I wasn't able to find (ping/ssh etc) my VM from my windows machine.
   I found the fix to be turning off my Windows firewall, and then resetting it by using the recommended settings.
Everything is good now.
Thanks to everyone who suggested what to do and helped.
You guys are great.
;)

---

### Post by ajgreeny on 2017-03-08
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

