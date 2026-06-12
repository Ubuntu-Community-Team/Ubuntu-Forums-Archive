---
title: "running sshd"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Marco_Polo on 2007-06-26
I've installed server edition 6.06 and am having trouble ssh'ing into my machine from elsewhere.  After running 'sudo /etc/init.d/ssh restart', I see that sshd is up by doing 'ps aux | grep sshd', which returns:
root     14068  0.0  0.2   4760  1032 ?        Ss   04:42   0:00 /usr/sbin/sshd

My IP is assigned through DHCP and it appears that port 22 is open.  'nmap IP' returns:
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-26 04:47 EDT
Interesting ports on 192.168... ::
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

I can ssh into the machine from my home account. 

However, the same nmap command from a separate machine returns:
Starting nmap 3.45 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-06-26 04:49 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap run completed -- 1 IP address (0 hosts up) scanned in 24.085 seconds

The attempt to ssh with -vv flag from the other machine yields:
OpenSSH_3.1p1, SSH protocols 1.5/2.0, OpenSSL 0x0090602f
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: restore_uid
debug1: ssh_connect: getuid 861 geteuid 0 anon 0
debug1: Connecting to 192.168... [192.168...] port 22.
debug1: Allocated local port 1023.
debug1: temporarily_use_uid: 861/878 (e=0)

No info is appended to /var/log/auth.log from this request.

Am I somehow blocking access to outside users?  'sudo iptables -L' returns:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Thanks for any ideas.  I'm new to these things, but enjoy learning so any advice is appreciated.

---

### Post by dfreer on 2007-06-26
Let me see if I got this straight. You are able to ssh into the ssh server from the local machine, like this?
**From SSH server:**
```
ssh localhost
```
But are unable to ssh into the server from another machine on the same LAN?
**From Client:**
```
ssh user@192.168.xxx.xxx
```

How did you install ssh? and if you made any modifications to /etc/ssh/sshd_config, can you post that file? Also, dumb question, but did you install a firewall on the server (not the iptables firewall, there's nothing wrong with it)?

---

### Post by Marco_Polo on 2007-06-26
Re: running sshd
Let me see if I got this straight. You are able to ssh into the ssh server from the local machine, like this?
From SSH server:
Code:

ssh localhost

But are unable to ssh into the server from another machine on the same LAN?
From Client:
Code:

ssh [email]user@192.168.xxx.xxx[/email]

That's right.

How did you install ssh? and if you made any modifications to /etc/ssh/sshd_config, can you post that file? Also, dumb question, but did you install a firewall on the server (not the iptables firewall, there's nothing wrong with it)?

I installed ssh with 'sudo apt-get install ssh' (or was it sshd?)  I did toy with /etc/ssh/sshd_config but have now restored the default version.  I also adjusted the permissions on ~/.ssh (was following advice from other posts.)  I installed firestarter with apt-get, but have it disabled (couldn't seem to configure it properly.)  

From a second remote machine 'ssh -vv IP' gives:
OpenSSH_3.7.1p2, SSH protocols 1.5/2.0, OpenSSL 0.9.7a Feb 19 2003
debug1: Reading configuration data /etc/openssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168... [192.168...] port 22.

Is the line 'needpriv 0' helpful?

Anyway, here's the /etc/ssh/sshd_config:

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by netztier on 2007-06-26
> **Marco_Polo said:**
> 

However, the same nmap command from a separate machine returns:
Starting nmap 3.45 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-06-26 04:49 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap run completed -- 1 IP address (0 hosts up) scanned in 24.085 seconds


Well, then do as nmap suggests:

```
nmap **-P0** <ip-address of ssh server>
```

And see if it now detects tcp/22 open. 

You might just as well do this (from the remote machine):
```
 telnet <ip-address of ssh server> 22 
```
And you should at least get a "Connected ..." message.

Also worth checking: see all open TCP ports on the SSH server itself:
```
 netstat -napt 
```
You should at least see a line that says that tcp/22 is in "LISTEN" state

You wouldn't have some form of netfilter/iptables, shorewall or Firestarter running on that machine, would you?


regards

Marc

---

### Post by Marco_Polo on 2007-06-26
nmap -P0 <ip-address of ssh server> returns:
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-26 19:12 EDT
Interesting ports on 192.168... :
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
Nmap finished: 1 IP address (1 host up) scanned in 0.363 seconds

That's good - my sshd and http servers are up and running.

telnet 192.168.xxx.xxx 22 from remote client returns:
Trying 192.168.xxx.xxx ...

But I can't see them from outside (I cannot create entries in /var/log/auth.d from outside by pinging/ssh'ing.)

netstat -napt from local returns:
tcp6       0      0 :::80                   :::*                    LISTEN     - 
tcp6       0      0 :::22                   :::*                    LISTEN     - 

I must be blocking these ports somehow, then because I cannot connect to either one (by ssh or http requests.)  So I guess this is a firewall issue?  I'm not aware that I'm running one.   I don't have experience with running servers, so I may have done something stupid.  Any ideas are welcome.  Thanks.

---

### Post by dfreer on 2007-06-26
try loading a live cd if you have one laying around into your CLIENT machine that is hooked up to the same LAN as your server. try ssh into the server from there. If it works, it could be your client has a highly restrictive firewall that is refusing to let SSH connect. If nothing else, it rules out the possibility that is a client problem and it is definitely a problem with the server.

Also, since ssh is fairly easy to run and install, you could purge your openssh-server package, clean your apt cache, and then reinstall:
```
sudo apt-get remove --purge openssh-server
sudo apt-get clean
sudo apt-get install openssh-server
```

This should get rid of all the configuration files for SSH and reinstall them to defaults, leaving you with a clean SSH install (no need to mess with it's config yet, might as well figure out your problem first).

---

### Post by Marco_Polo on 2007-06-26
Am I misidentifying myself?  I get my IP by DHCP and know it from the inet field in ifconfig's output.  But if my ports are in LISTEN state and I don't get activity in the /var/log/auth.log, I could be ssh'ing a different host which does not respond.  I'm not sure if I've got my hostname and /etc/hosts file configured correctly.  My iptables are clear, so the ssh requests must not be arriving.  Does that prime anyone for ideas? :)

---

### Post by dfreer on 2007-06-26
*confused* why are you trying to connect via hostnames? why not just use the actual IP address of the server? It's your LAN, why would there be another SSH server?
Your /etc/hostname should be just the name of your server, such as mylaptop or danpc. And ONLY that name, it is pretty picky and a pain to fix because sudo relies on it. Also, it absolutely needs to be the same in /etc/hosts file as well.

your /etc/hosts on the server should look like this:
```
127.0.0.1       localhost.localdomain localhost
127.0.1.1       **the_name_in_/etc/hostname_here**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Marco_Polo on 2007-06-26
My ssh client on remote machine works fine.  I login to other servers.  My /etc/hostname file has only the server name 'MarcoPolo' and /etc/hosts follows:
127.0.0.1	localhost
127.0.1.1	MarcoPolo

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

If my ISP is blocking port 22 would the client get a rejection or silence (I suspect a rejection?)  Anyway to (dis)prove that hypothesis?  

I have reinstalled openssh-server with apt-get remove and apt-get install.  Same behavior - by the way I am using the IP address to attempt my logins - I just suspected that I could have it wrong.  I noticed that when I use this machine as a client, the other server reports a different IP address logged into it - it's an embarq dsl connection.  
Anyway, thanks for all the help so far.

---

### Post by dfreer on 2007-06-27
ok, it stills sounds like there is some sort of communication error going on here, at least in my mind. Either this is due to your being slightly vague with terms (not specifying full IP addresses, saying you are trying to SSH from "elsewhere", etc), or I'm just really tired and missing something important (if anyone else is reading this, any thoughts?)
You are talking about your ISP blocking port 22, yet if you are on a LAN your ISP would have absolutely no influence of what ports you use locally. Also, you are talking about the "other server" reporting a "different IP address" logged into it, which sounds like you are trying to do SSH from across the internet, not across a LAN.
So to avoid any further confusion, *can you please be as specific as possible*? Really, as long as you don't give us a username/password/globally routable IP address (something NOT in the 192.168.xxx.xxx range), there are no reasons for you to be vague. It sounds like you know linux at times, and how to use SSH, so it may be that I'm just treating you like a n00b in which case I'll just back off the thread and give someone else a chance to help you, hopefully one smarter than me lol.

One of the first questions I asked was whether you...
> are unable to ssh into the server from another machine **on the same LAN?**

This would mean both the **SSH Server** and the **SSH Client (which is another ubuntu machine)** would be sitting somewhere within your house/office/whatever, both machines are hooked up in some way to a common router also sitting in this location, and they are both on the same subnet. If you ran ifconfig on both machines, they would produce identical output for Bcast, Mask, and the inet addr on each would be nearly identical. 
If this is the case, then forgive me for repeating the obvious. I don't think I can help you any further as I am out of ideas. If no one else has ideas, I would try a reinstall of the server, or perhaps switch distros and try a debian server out. Is firestarter for sure completely uninstalled?


If this is not the case, as in you have the **SSH Server** plugged into router at your office, and your **SSH client** is a laptop that is plugged into a router at your house, or perhaps your **SSH client** is wireless and your **SSH server** isn't, you may be dealing with an ISP that is blocking port 22, or a firewall on your router that needs port forwarding set up, or just a need to know the external IP address of the **SSH server**. If this is the case at all, I can surely help you fix this problem and get everything working right.

I'm not suggesting your stupid or anything, I'm just trying to figure this out. Since SSH runs straight from install, and requires only an network connection and a functional PC to work, it is really perplexing that this isn't working for you *confused as ever*

EDIT: as for your question about whether to check if your ISP blocks ports, try this website [www.canyouseeme.org](www.canyouseeme.org) or try just calling them up and asking them. also, uninstall of SSH is only really effective if you use the --purge parameter as well. In the case of my friend who uses Embarq internet, they provided him with a modem that has a router **built into it**, that converts the DSL line to an ethernet cable. He then had the ethernet cable from the modem plugged into his wireless router. This means two routers providing NAT, so two port fowardings to enable.

---

