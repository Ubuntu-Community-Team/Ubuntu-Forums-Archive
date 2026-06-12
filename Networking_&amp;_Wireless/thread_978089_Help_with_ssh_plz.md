---
title: "Help with ssh plz"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by nphls on 2008-11-10
Hi there.

I'm running Ubuntu as a virtual machine under Windows XP.
I'd like to be able to connect from any windows machine to Ubuntu using putty.

I can already start the ssh server:
```
$ sudo /etc/init.d/ssh start
* Starting OpenBSD Secure Shell server sshd                             [ OK ]

```

But when I try to connect from windows with putty i get this error: "Network error: Connection refused"

I know that some configurations still have to be done I just don't know which and how.

Can anybody help me out?

Thanks in advance.

---

### Post by dmizer on 2008-11-11
Please post the contents of /etc/ssh/sshd_config

---

### Post by nphls on 2008-11-11
> **dmizer said:**
> please post the contents of /etc/ssh/sshd_config

Here it is:
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
```

---

### Post by dmizer on 2008-11-11
Okay, that looks good. Do you have a firewall on your Windows box, or on your Ubuntu box?

Try this one please:
```
sudo iptables -L
```

---

### Post by nphls on 2008-11-11
On Windows I have the Windows firewall (i should get a new one!, i know). On Ubuntu I don't have a firewall.

$ sudo iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by mtausig on 2008-11-11
Before going too dep into the sshd configuration: Can you ping the virtual machine from windows?

---

### Post by depele on 2008-11-11
Try to turn off windows firewall.
Or open port 22 in (exeption in windows)firewall

grtz..

---

### Post by nphls on 2008-11-11
> **mtausig said:**
> Before going too deep into the sshd configuration: Can you ping the virtual machine from windows?

On Windows I entered cmd and typed in "ipconfig" and i get two Ethernet adapter VMware Network Adapter ( 1 and 8 ) and don't know which one is the one. Anyway, I can successfully ping both.

```
Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.202.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.216.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Wireless Network Connection 3:

        Connection-specific DNS Suffix  . : local.lan
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
```

On Ubuntu I entered the console and typed in "ifconcfig". I also can from windows ping the ip from virtual Ubuntu ( 192.168.202.128 )

```

eth1      Link encap:Ethernet  HWaddr 00:0C:29:A6:56:C0  
          inet addr:192.168.202.128  Bcast:192.168.202.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea6:56c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:980125 (957.1 KB)  TX bytes:48271 (47.1 KB)
          Interrupt:16 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


> **depele said:**
> Try to turn off windows firewall.
Or open port 22 in (exception in windows)firewall


I did that but I still can't connect.

---

### Post by mtausig on 2008-11-11
type "tail -f /var/log/syslog" in the ubuntu box and then try to login with ssh again. Please post the lines that appear.

---

### Post by dmizer on 2008-11-11
Can you post a screen shot of the putty configurations?

---

### Post by nphls on 2008-11-11
> **mtausig said:**
> type "tail -f /var/log/syslog" in the ubuntu box and then try to login with ssh again. Please post the lines that appear.

When I try to connect from windows with putty to my IP (the one I get from my ISP. The one I get from [www.checkip.org](www.checkip.org)) I continue to get the same error: "Network error: Connection refused". No lines appear in the virtual Ubuntu console after that. 
I don't know if the previous lines are important, but here they are:

```
Nov 11 17:01:00 feuplive-virtual dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov 11 17:01:00 feuplive-virtual NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Nov 11 17:01:01 feuplive-virtual dhclient: DHCPOFFER from 192.168.202.254
Nov 11 17:01:01 feuplive-virtual dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov 11 17:01:01 feuplive-virtual dhclient: DHCPACK from 192.168.202.254
Nov 11 17:01:01 feuplive-virtual avahi-daemon[4521]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.202.128.
Nov 11 17:01:01 feuplive-virtual avahi-daemon[4521]: New relevant interface eth1.IPv4 for mDNS.
Nov 11 17:01:01 feuplive-virtual avahi-daemon[4521]: Registering new address record for 192.168.202.128 on eth1.IPv4.
Nov 11 17:01:02 feuplive-virtual NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov 11 17:01:02 feuplive-virtual dhclient: bound to 192.168.202.128 -- renewal in 862 seconds.
```


> **dmizer said:**
> Can you post a screen shot of the putty configurations?

The putty configurations are the default ones. Do you still want a screen shot? If yes, of which settings (Session, Terminal, Window, Connection, SSH)?

I'd like to thank you all for trying to help me out. I really appreciate it. ;-)

---

### Post by nphls on 2008-11-11
I forgot to say something which is probably relevant.

I'm behind a router. So I have to forward port 22, right?

My doubt is: should I forward port 22 (both TCP and UDP?) to the IP I get from "ifconfig" from virtual Ubuntu 
or to one of the IPs I get from "ipconfig" on windows (VMnet8 or VMnet1?)?

---

### Post by dmizer on 2008-11-11
> **nphls said:**
> I forgot to say something which is probably relevant.

I'm behind a router. So I have to forward port 22, right?

My doubt is: should I forward port 22 (both TCP and UDP?) to the IP I get from "ifconfig" from virtual Ubuntu 
or to one of the IPs I get from "ipconfig" on windows (VMnet8 or VMnet1?)?

Okay, is Windows your virtual machine or is Ubuntu your virtual machine? What computer are you trying to ssh from? Where are you trying to ssh from (inside your own network, or from another location)? As for putty screen shot, I wanted to know what you enter for the Session under "host name", but I couldn't remember putty well enough to tell you what exactly I was looking for.

---

### Post by nphls on 2008-11-11
> **dmizer said:**
> Okay, is Windows your virtual machine or is Ubuntu your virtual machine? What computer are you trying to ssh from? Where are you trying to ssh from (inside your own network, or from another location)? As for putty screen shot, I wanted to know what you enter for the Session under "host name", but I couldn't remember putty well enough to tell you what exactly I was looking for.

> **nphls said:**
> 
I'm running Ubuntu as a virtual machine under Windows XP.
I'd like to be able to connect from any windows machine to Ubuntu using putty.

So, I have a windows XP installed on the hard drive and I'm using VMware to run Ubuntu.


About putty, on "host name" I'm entering mydomain.homelinux.com (a free dynamic DNS from dyndns.com which is being updated automatically)

Once again, thanks a lot for your help.

---

### Post by dmizer on 2008-11-11
> **nphls said:**
> So, I have a windows XP installed on the hard drive and I'm using VMware to run Ubuntu.


About putty, on "host name" I'm entering mydomain.homelinux.com (a free dynamic DNS from dyndns.com which is being updated automatically)

Once again, thanks a lot for your help.

So you are attempting to ssh from the Windows computer (putty on the same computer as vmware) into the Ubuntu computer? If that's the case, you do not need a mydomain.homelinux.com, just enter the ip address of the ubuntu computer [noparse](192.168.202.128)[/noparse] in the "host name" field.

---

### Post by nphls on 2008-11-12
> **dmizer said:**
> So you are attempting to ssh from the Windows computer (putty on the same computer as vmware) into the Ubuntu computer? If that's the case, you do not need a mydomain.homelinux.com, just enter the ip address of the ubuntu computer [noparse](192.168.202.128)[/noparse] in the "host name" field.

I'm testing if ssh conncetion is working properly from my computer (if it doesnt work from the inside it probably won't work from the outside).

What I'd like to be able to do is to connect from other windows computer (not mine) to virtual Ubuntu.

---

### Post by dmizer on 2008-11-12
> **nphls said:**
> I'm testing if ssh conncetion is working properly from my computer (if it doesnt work from the inside it probably won't work from the outside).

What I'd like to be able to do is to connect from other windows computer (not mine) to virtual Ubuntu.

Well you're running into a few problems then.

First, your router is most likely not capable of looping back a request. Or in other words, you probably can't ssh to mydomain.homelinux.com. Routers often get confused when mydomain.homelinux.com essentially comes and goes from/to the same location.

Second, your Ubuntu computer is not getting an IP address from your router (vmware is handing Ubuntu's ip address via a private subnet), so as far as your router is concerned, your Ubuntu box doesn't even exist. So, even if you are outside your network and have ssh forwarded to your Windows box, you still won't reach your Ubuntu computer.

So, you'll have to do a few things to get around this problem. If you need to access the Ubuntu guest from the web, you'll need to enable network bridging in vmware. That way, your Ubuntu computer will get an IP address from the router, and the router can be configured to forward port 22 to the Ubuntu IP address.

You'll also have to be aware that as long as you are on the same network as your Ubuntu computer, you will most likely be unable to use the mydomain.homelinux.com address. Just use the Ubuntu IP address instead.

There are other ways around this, but for the testing purposes I'm just trying to give you enough information to get things set up correctly, and understand the difference between how your router treats requests from inside your network vs. how your router treats requests from outside your network (LAN vs WAN).

Hope that helps.

---

### Post by nphls on 2008-11-25
Thanks to you all for all your help.

---

