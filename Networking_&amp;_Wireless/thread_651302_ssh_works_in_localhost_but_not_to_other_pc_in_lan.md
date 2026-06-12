---
title: "ssh works in localhost but not to other pc in lan"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by kr0n1x on 2007-12-27
**[SIZE="6"][COLOR="Red"]UPDATE: this post is old, read starting from the 10° post![/COLOR][/SIZE]**

hi, i readed the wiki (italian and english) of OpenSSH and i installed ssh-server in all pc (i've 2 pc in my home lan, 1 with ubuntu gutsy and 1 with fluxbuntu)

in all 2 pc, when i try ssh localhost, it works.
but if i try ssh user@ip or other similar command, it doesn't work.

ssh works only in localhost.

what can be the problem???

in past, i tried ssh with gutsy and feisty (gutsy in 1 pc and feisty in the other) and ssh worked well. why now not??? can the problem be in fluxbuntu?

if you need more info, ask me! 

thanks, bye

---

### Post by trobbins on 2007-12-27
Run this command and post the output:

```
 netstat -t -a | grep ssh  
```

It should look something like this:

trobbins@fasterone:~$ netstat -t -a | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN     

If you see tcp6, but not just tcp, you will need to configure SSH to listen using IPV4.  See this previous thread outlining how to do this:

[http://ubuntuforums.org/showthread.php?t=644045&highlight=IPV4](http://ubuntuforums.org/showthread.php?t=644045&highlight=IPV4)

---

### Post by kr0n1x on 2007-12-27
i need to have the 2 pc on?? because in this moment i've fluxbuntu machine off.

here is the output (in ubuntu gutsy, the only pc ON now):
```
pasquale@pasquale-desktop:~$ netstat -t -a | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN     
pasquale@pasquale-desktop:~$
```

what i have to do?

---

### Post by Dr Small on 2007-12-27
If you are ssh'ing from system A to system B (scenario).

System A needs to have a ssh client (which comes by default on ubuntu, and most distributions)

System B needs to have the ssh-server (openssh-server).
It will also need to have port 22 opened on it's firewall.

Now, from System A, let's connect to system B:
```
ssh user@systemb
```

You should now be able to connect to system b (the system with the ssh server on it).
If you want to do this visa versa, then just install openssh-server on each system, and make sure to open port 22 on each system, to allow inbound connections on port 22.

Dr Small

---

### Post by kr0n1x on 2007-12-27
openssh-server is installed in both machines.

i will try opening port 22 (tcp?).

anyway... in past... when ssh worked with gutsy and feisty ... i didn't have need to open ports on my router...

i will try to open ports tomorrow... now i can't.

thanks, bye

---

### Post by kr0n1x on 2007-12-28
i opened the ports 22 (local) in both 2 pc in my router. but ssh still doesn't work.

i repeated the command, this time with both pc ON:
```
pasquale@pasquale-desktop:~$ netstat -t -a | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN     
pasquale@pasquale-desktop:~$
```

---

### Post by kr0n1x on 2008-01-06
i was able to connect to my pc (the ubuntu gutsy 64 bit) from a pc on internet... and i wasn't able to connect from a pc in my lan  XD auhauah
anyway i deleted fluxbuntu from the amd1800+ pc, i will install xubuntu on it and i will retry the ssh connection :)

bye

---

### Post by Digger78 on 2008-01-06
you might want to try adding each machines IP  and hostname to
** /etc/hosts** & **/etc/hosts.allow**
e.g
```

192.168.1.2 pasquale-desktop
```

Do you know what i mean?

---

### Post by kr0n1x on 2008-01-06
understand... but i didn't need to do that for the "internet" pc..(out of the lan)
why i need to do that for a pc in my lan? :( i can try anyway...and maybe i've already did this... i don't remember
anyway i didn't add this ip (the "on internet" pc) in my ubuntu gutsy pc.

---

### Post by kr0n1x on 2008-01-12
**[SIZE="6"][COLOR="Red"]UPDATE - no fluxbuntu now...[/COLOR][/SIZE]**

i installed the new OS in my old pc. now i haven't fluxbuntu.

now this is my situation:
conroe6300 = the name of the pc with Ubuntu Gutsy 7.10 64bit (i'm writing from it)
amd1800 = the name of the pc with the new OS installed, Ubuntu Server edition 7.10 i386

i installed openssh-server in the new system (amd1800) and i set it reading the wiki.

i modified the .ssh/authorized_keys file in both pc (after the creation of dsa keys), and i enabled the PubkeyAuthentication too.

restarted ssh server, opened port in my router.

unfortunately, i'm not able to connect to my pc :( both...

i can't connect from conroe6300 to amd1800 and viceversa.

here is my sshd_config file in conroe6300 pc:

```
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
AuthorizedKeysFile	%h/.ssh/authorized_keys

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

UsePAM yes
```

that file is equal to the amd1800 file one, only the port changes... it is 23 in amd1800 pc. (port 22 and 23 are opened in my router).

what can i do??

---

### Post by chippy99 on 2008-01-12
Set both ports to 22 in the config file. IF they are both listening on different ports they will not connect  (unless you explicitly specify the port number).

---

### Post by kr0n1x on 2008-01-12
> **chippy99 said:**
> Set both ports to 22 in the config file. IF they are both listening on different ports they will not connect  (unless you explicitly specify the port number).

they was equal... and didn't work. now i set ports to 22 in conroe6300 and 23 in amd1800.

how can i try to connect to a pc specifying the port?
```
ssh user@pcname:port
```

if the command is correct, it doesn't work...
> ssh: amd1800:23: Name or service not known
i tried also with local ip:port (192.168.x.x:23) but nothing..

---

### Post by kr0n1x on 2008-01-12
more commands tried:
```
pasquale@conroe6300:~$ ssh -p 23 pasquale@192.168.1.174
```
and it stays as is..without any reply... this is my problem :(

```
pasquale@conroe6300:~$ ping 192.168.1.174
PING 192.168.1.174 (192.168.1.174) 56(84) bytes of data.

--- 192.168.1.174 ping statistics ---
98 packets transmitted, 0 received, 100% packet loss, time 97193ms

pasquale@conroe6300:~$
```

---

### Post by kr0n1x on 2008-01-12
more informations about my machines:

ifconfig on conroe6300 (eth1, 192.168.1.75):

```
pasquale@conroe6300:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:4F:1B:FA:9E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:08:40:EA  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:630675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:659306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:418597470 (399.2 MB)  TX bytes:298969780 (285.1 MB)
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:323910 (316.3 KB)  TX bytes:323910 (316.3 KB)

pasquale@conroe6300:~$
```

ifconfig on amd1800 (eth0, 192.168.1.174):

```
eth0      Link encap:Ethernet  HWaddr 00:08:54:50:A3:03  
          inet addr:192.168.1.174  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe50:a303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38067779 (36.3 MB)  TX bytes:1130050 (1.0 MB)
          Interrupt:10 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


route -n on conroe6300:

```
pasquale@conroe6300:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
pasquale@conroe6300:~$
```

sudo iptables -L on conroe6300:

```
pasquale@conroe6300:~$ sudo iptables -L
[sudo] password for pasquale:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
pasquale@conroe6300:~$
```

i'm writing all possible infos :( if you need more.. ask me.

thanks, bye

---

### Post by Digger78 on 2008-01-12
try this on conroe6300

```
sudo ifconfig eth0 down
```

then try connecting again

---

### Post by kr0n1x on 2008-01-12
> **Digger78 said:**
> try this on conroe6300

```
sudo ifconfig eth0 down
```

then try connecting again

i did your command, and after i tried:
```
ssh -p 23 pasquale@192.168.1.174
```

but nothing :( it stays without any reply... i can only press ctrl+c

i'm reading this article: [http://ubuntu-tutorials.com/2008/01/12/disabling-ssh-connections-on-ipv6/](http://ubuntu-tutorials.com/2008/01/12/disabling-ssh-connections-on-ipv6/)

can the problem be ipv6? anyway i think not.. because in past i was able to connect form internet to my conroe6300 without problems :( and in local lan i wasn't able to do that!

---

### Post by Digger78 on 2008-01-12
also try binding sshd to listen on  IP  address

 edit** /etc/ssh/sshd_config** on both systems

for conroe6300  

```
ListenAddress 192.168.1.75
```

for amd1800

```
ListenAddress 192.168.1.175
```

restart ssh server

```
sudo /etc/init.d/ssh restart
```

---

### Post by Digger78 on 2008-01-12
lol, just had a quick look at that tutorial and it says the same thing. :)

---

### Post by kr0n1x on 2008-01-12
did, but nothing.

forever the same problem...

cause this didn't solve my problem, i put a # before *Address Listen localip*, to keep the config file clean from much edit.. :)

---

### Post by kr0n1x on 2008-01-13
in conroe6300 i've also gentoo and debian. from these distro i can ping amd1800.
from ubuntu i can't :( ping amd1800.

then the problem isn't in amd1800 pc, but in conroe6300 and in ubuntu desktop 7.10, because other distro installed works great in ping and ssh to amd1800 :)

what files i need to check in ubuntu??? thanks, bye

---

