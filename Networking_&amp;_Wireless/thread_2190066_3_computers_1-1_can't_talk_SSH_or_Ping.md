---
title: "3 computers 1-1 can't talk??? SSH or Ping"
date: 2013-11-25
forum: Networking &amp; Wireless
---

### Post by grandrigo on 2013-11-25
Lets say I have 3 computers all hooked up in the network:
Linux1
Linux2 
LiveDuo

1. In Linux1, I can ssh and ping Linux2 with no problem
2. In Linux2, I can ssh and ping Linux1 with no problem

3. In Linux1, I can ssh and ping LiveDuo with no problem
4. In Linux2, I CAN'T ssh or ping LiveDuo ??? Why ??

I restarted ssh in Linux2 and didn't work. I also found that in arp -n the IP address of LiveDuo was listed in Linux2 so I deleted and it didn't help.
Any other suggestions??

---

### Post by The Cog on 2013-11-25
I would start by using tcpdump to watch what packets go between the machines. 
Run this command on linux2 and then try the ping in another prompt:
```
sudo tcpdump -npe
```
And perhaps compare with the same test on linux1 or post the trace here if you're having difficulty with it.

Edit:
Is it possible that another PC has the same IP address as linux2, and LiveDuo is forwarding to the other one? I don't know what LiveDuo is.

---

### Post by grandrigo on 2013-11-25
LiveDuo is like a time machine but acts as another computer since I can ssh to it back and forth from linux1.  Which files are specific for Ubuntu that might have that IP block or something strange?

---

### Post by grandrigo on 2013-11-27
Any other suggestions?

---

### Post by grandrigo on 2013-11-27
Hello all,
I have some trouble with my Ubuntu machine using ssh. I was wondering what files are executed/read/needed during the ssh process? For example: /etc/host.cong or ~/.ssh/*

Thanks in advance,

---

### Post by Lars Noodén on 2013-11-27
Are you talking about the client or the server?  

For the client, no files are really needed, but if they exist ~/.ssh/config and /etc/ssh/ssh_config will be read.

---

### Post by grandrigo on 2013-11-27
There is something wrong with my ssh command in one of my specific computer [http://ubuntuforums.org/showthread.php?t=2190066&p=12859326#post12859326](http://ubuntuforums.org/showthread.php?t=2190066&p=12859326#post12859326) 

I was wondering what files are being accessed when I execute this command? Or what files are needed for it? 
For example:
~/.ssh*
/etc/host.conf 

??

---

### Post by jonobr on 2013-11-27
Hello


Just wondering what makes you think there is something wrong with the command on that computer.
I recommend running the command the cog suggested.
It should show you if ssh packets are going to the target and id they are being received.

If you really suspect ssh is a problem you could always remove and readd it

---

### Post by bab1 on 2013-11-27
> **grandrigo said:**
> There is something wrong with my ssh command in one of my specific computer [http://ubuntuforums.org/showthread.php?t=2190066&p=12859326#post12859326](http://ubuntuforums.org/showthread.php?t=2190066&p=12859326#post12859326) 
> Not impossible but mot likely the problem is somewhere other than ssh

I was wondering what files are being accessed when I execute this command?  Or what files are needed for it? 

The ssh binary is what is called.  It is located at /usr/bin/ssh.  You can see it by using *strace*.  The very first this called is this: *execve("/usr/bin/ssh"*
> 

For example:
~/.ssh*
/etc/host.conf 

??
Not sure what the last thing is.

If you can't ping the device then you won't be able to ssh to it either.  What do you get when you ping the device.  Do you use the IP address or hostname?

Since this is really an extension of the first question why did you start a second thread?

---

### Post by cariboo on 2013-11-27
Please don't start multiple threads on the same subject, I have merged 3 of your threads.

---

### Post by grandrigo on 2013-12-04
I can't ping to the device from that computar (linux1) but I can ping anywhere else. I can also ping and ssh to LiveDuo from any other computer

---

### Post by Iowan on 2013-12-04
> **grandrigo said:**
> I can't ping to [COLOR="#FF0000"]the device[/COLOR] from that computar (linux1) but I can ping anywhere else. I can also ping and ssh to LiveDuo from any other computer"the device" is the LiveDuo machine?

---

### Post by grandrigo on 2013-12-04
yes "the device" is the LiveDuo. I have an identical computer with the identical settings Linux2 and I am able to ssh to LiveDuo. This problem started when another person tried enabling the samba server btw...

---

### Post by Iowan on 2013-12-04
> **grandrigo said:**
> This problem started when another person tried enabling the samba server btw...What Samba server? 
On/from which machine?
Have you compared the routing tables (**route -n**) between the two machines(Linux1 and Linux2)?

---

### Post by bab1 on 2013-12-04
> **grandrigo said:**
> yes "the device" is the LiveDuo. I have an identical computer with the identical settings Linux2 and I am able to ssh to LiveDuo. This problem started when another person tried enabling the samba server btw...

You need to help us a little more than just "it doesn't work".  What is IP address of the "device" you are trying to ping?  What is the exact command you used?  What is the IP address of the host you are pinging from?  What is the the error message you get when the ping fails?

Does the "device" have a hostname?  Does it have a NETBIOS name?  Have you configured Windows style sharing?  How did you do that?  What CLI commands?  What GUI dialog?

---

### Post by grandrigo on 2013-12-05
I'm sorry but it looks simpler than that. I can provide you the NETBIOS name, CLI commands or GUI dialog if you walk me thorugh. Though everything is done from command line.
Here is a review.

**Devices:**
Linux1 (Ubuntu 12.04)
Linux2 (Ubuntu 12.04)
LiveDuo (MyBook Live Duo from western digital with ssh enabled) --> I'll try its ip: 10.50.4.43 instead to avoid DNS conflicts



**The Problem**:
Linux1 can't connet to LiveDuo but it can connect to any other device such as Linux2 or any other machine! Any other devices (e.g. Linux2) can connect to LiveDuo and Linux1

**Replication:**
_Linux1 (sshing to Linux2):_
<username>@Linux1#$ ssh Linux2
<username>@Linux1's password: 
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-54-generic x86_64)
.
.
.

_#PROBLEM: **Linux1 (sshing to LiveDuo):**_
<username>@Linux1#$ ssh root@10.50.4.43
ssh: connect to host 10.50.4.43 port 22: No route to host       #THIS IS THE PROBLEM!!!



_Linux1 pinging to Linux2:_
<username>@Linux1#$ping Linux2
PING Linux2 (10.50.4.5) 56(84) bytes of data.
64 bytes from Linux2.<some_domain> (10.50.4.5): icmp_req=1 ttl=64 time=0.139 ms
64 bytes from Linux2.<some_domain> (10.50.4.5): icmp_req=2 ttl=64 time=0.134 ms
.
.
.

_#PING PROBLEM Linux1 pinging to LiveDuo:_            ##!!! AGAIN A PROBLEM!
<username>@Linux1#$ping 10.50.4.43
PING 10.50.4.43 (10.50.4.43) 56(84) bytes of data.
From 10.50.4.59 icmp_seq=9 Destination Host Unreachable
From 10.50.4.59 icmp_seq=10 Destination Host Unreachable
From 10.50.4.59 icmp_seq=11 Destination Host Unreachable
From 10.50.4.59 icmp_seq=12 Destination Host Unreachable


[U]
Linux1 tracepath to Linux2:  [/U]             
<username>@Linux1#$ tracepath Linux2 1:  Linux1.<some_domain>                               0.068ms pmtu 1500
 1: Linux2.<some_domain>                                 0.263ms reached
 1:  Linux2<some_domain>                              0.305ms reached
     Resume: pmtu 1500 hops 1 back 64 


_#PROBLEM** Linux1 tracepath to LiveDuo**_**: **                 #! PROBLEM....NOTHING IN RESPONSE???
<username>@Linux1#$ tracepath LiveDuo
 1:  Linux2.<domain...>                                 0.058ms pmtu 1500
 1:  Linux2.<domain...>                                 2996.323ms !H
     Resume: pmtu 1500 

**Replication in Linux2 to LiveDuo:**

_ Linux2 (sshing to LiveDuo):_
<username>@Linux2#$ ssh root@10.50.4.43
root@10.50.4.43's password: 
Linux KUADCLiveDUO 2.6.32.11-svn70860 #1 Thu May 17 13:32:51 PDT 2012 ppc
Disclaimer: SSH provides access to the network device and all its 
content, only users with advanced computer networking and Linux experience 
should enable it. Failure to understand the Linux command line interface 
can result in rendering your network device inoperable, as well as allowing 
unauthorized users access to your network. If you enable SSH, do not share 
the root password with anyone you do not want to have direct access to all 
the content on your network device.

KUADCLiveDUO:~# 


_Linux2 pinging to LiveDuo:_    
<username>@Linux2#$ ping 10.50.4.43
ping 10.50.4.43
PING 10.50.4.43 (10.50.4.43) 56(84) bytes of data.
64 bytes from 10.50.4.43: icmp_req=1 ttl=64 time=0.180 ms
64 bytes from 10.50.4.43: icmp_req=2 ttl=64 time=0.183 ms
64 bytes from 10.50.4.43: icmp_req=3 ttl=64 time=0.193 ms




_Linux2 tracepath LiveDuo_:
<username>@Linux2#$ tracepath 10.50.4.43
 1:  Linux2.<domain...>                               0.066ms pmtu 1500
 1:  LiveDuo.<domain...>                                 0.298ms reached
 1:  LiveDuo.<domain...>                                0.247ms reached
     Resume: pmtu 1500 hops 1 back 64 


**Replication in LiveDuo:**
_Sshing to Linux1 and Linux2:_
[U]
##PROBLEM HERE!!!
[/U]<username>@LiveDuo#$ ssh Linux1
ssh: connect to host Linux1 port 22: Connection timed out

<username>@LiveDuo#$ ssh Linux2
<username>@Linux2's password: 
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-54-generic x86_64)[U]
.
.
.


Pinging to Linux1 and Linux2:
[/U]
#PROBLEM HERE!! 
<username>@LiveDuo#$ ping Linux1
PING Linux1.<some_domain> (10.50.4.59) 56(84) bytes of data.
.
.
.(needed to cancel after a while...)
.
--- Linux1.<some_domain> ping statistics ---
79 packets transmitted, 0 received, 100% packet loss, time 78162ms



<username>@LiveDuo#$ping Linux2
PING Linux2.<some_domain>(10.50.4.5) 56(84) bytes of data.
64 bytes from Linux2.<some_domain> (10.50.4.5): icmp_seq=1 ttl=64 time=0.183 ms
64 bytes from Linux2.<some_domain> (10.50.4.5): icmp_seq=2 ttl=64 time=0.145 ms
64 bytes from Linux2.<some_domain> (10.50.4.5): icmp_seq=3 ttl=64 time=0.193 ms
^C
--- Linux2.<some_domain> ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.145/0.173/0.193/0.025 ms

[U]Traceroute to Linux1 and Linux2:


#PROBLEM HERE
<username>@LiveDuo#$traceroute Linux1
[/U]traceroute to Linux1 (10.50.4.59), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
<username>@LiveDuo#$traceroute Linux2
traceroute Linux2
traceroute to Linux2 (10.50.4.5), 30 hops max, 40 byte packets
 1  Linux2.kumc.edu (10.50.4.5)  0.153 ms  0.099 ms  0.091 ms



*I hope this is more readable and honestly I dont know whay is going on with Linux1. Any other suggestions, commands that I should run? I tried uninstalling openssh from the software center in Linux1 but again it doesn't even ping or tracepath to LiveDuo. Any other suggestions?
I am not a network expert but I do have a little understanding on how to troubleshoot this problem but so far I have no other tries :/ Any suggestions will be helpful!

---

### Post by The Cog on 2013-12-05
You still haven't done the trace that I suggested in post #2. Why not?

If you refuse to do that, then post the output of these commands run on both linux1 and linux2:
```
ifconfig
route -n 
arp -an
```

---

### Post by grandrigo on 2013-12-05
Sorry I did the tcpdump but there are so much output that I can't copy and paste or observe the packages. Probably becuase I ssh to connect to that machine. Anyway, here are the outputs of each command:

In Linux1:
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:39:42:6e  
          inet addr:10.50.4.59  Bcast:10.50.4.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe39:426e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151131925 (151.1 MB)  TX bytes:406356233 (406.3 MB)
          Interrupt:21 Memory:febe0000-fec00000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1985980444 (1.9 GB)  TX bytes:1985980444 (1.9 GB)




~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.50.4.1       0.0.0.0         UG    0      0        0 eth0
10.50.4.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0



~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
10.50.4.5                ether   00:25:64:38:8d:88   C                     eth0
10.50.4.1                ether   70:ca:9b:18:63:45   C                     eth0
10.50.4.82               ether   3c:07:54:7e:06:1e   C                     eth0
10.50.4.45               ether   00:13:72:0b:e5:54   C                     eth0

```





In Linux2:
```
ifconfig
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:38:8d:88  
          inet addr:10.50.4.5  Bcast:10.50.4.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe38:8d88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15742026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3531188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5493733098 (5.4 GB)  TX bytes:1087893770 (1.0 GB)
          Interrupt:21 Memory:febe0000-fec00000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:714570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:714570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2773258512 (2.7 GB)  TX bytes:2773258512 (2.7 GB)



~#$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.50.4.1       0.0.0.0         UG    0      0        0 eth0
10.50.4.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0





~$ arp -an
? (10.50.4.82) at 3c:07:54:7e:06:1e [ether] on eth0
? (10.50.4.43) at 00:90:a9:bd:e6:12 [ether] on eth0
? (10.50.4.29) at 10:9a:dd:43:25:8f [ether] on eth0
? (10.50.4.73) at 00:23:24:31:59:fd [ether] on eth0
? (10.50.4.59) at 00:24:e8:39:42:6e [ether] on eth0
? (10.50.4.1) at 70:ca:9b:18:63:45 [ether] on eth0
```

---

### Post by bab1 on 2013-12-05
> **grandrigo said:**
> I'm sorry but it looks simpler than that. I can provide you the NETBIOS name, CLI commands or GUI dialog if you walk me thorugh. Though everything is done from command line.
Here is a review.

**Devices:**
Linux1 (Ubuntu 12.04)
Linux2 (Ubuntu 12.04)
LiveDuo (MyBook Live Duo from western digital with ssh enabled) --> I'll try its ip: 10.50.4.43 instead to avoid DNS conflicts


**The Problem**:
Linux1 can't connet to LiveDuo but it can connect to any other device such as Linux2 or any other machine! 
Any other devices (e.g. Linux2) can connect to LiveDuo and Linux1

**Replication:**
_Linux1 (sshing to Linux2):_
<username>@Linux1#$ ssh Linux2
<username>@Linux1's password: 
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-54-generic x86_64)

_#PROBLEM: **Linux1 (sshing to LiveDuo):**_
<username>@Linux1#$ ssh root@10.50.4.43
ssh: connect to host 10.50.4.43 port 22:[COLOR="#FF0000"] No route to host  [/COLOR]     #THIS IS THE PROBLEM!!!


_Linux1 pinging to Linux2:_
<username>@Linux1#$ping Linux2
PING Linux2 (10.50.4.5) 56(84) bytes of data.
64 bytes from [COLOR="#FF0000"]<redacted> (10.50.4.5)[/COLOR]: icmp_req=1 ttl=64 time=0.139 ms
64 bytes from <redacted> (10.50.4.5): icmp_req=2 ttl=64 time=0.134 ms
.
.
.

_#PING PROBLEM Linux1 pinging to LiveDuo:_            ##!!! AGAIN A PROBLEM!
<username>@Linux1#$ping 10.50.4.43
PING 10.50.4.43 (10.50.4.43) 56(84) bytes of data.
From [COLOR="#FF0000"]10.50.4.59 icmp_seq=9 Destination Host Unreachable[/COLOR]
From 10.50.4.59 icmp_seq=10 Destination Host Unreachable
From 10.50.4.59 icmp_seq=11 Destination Host Unreachable
From 10.50.4.59 icmp_seq=12 Destination Host Unreachable




Just skimming the information you have provided I see red flags.    

The first is the error:  No route to host.  This suggests that the two devices are not on the same network and there is either no gateway configured on the host trying to ssh or there is no route defined on that host.  Are both hosts part of the same network?  If not you have a problem as the 10.0.0.0 /8 network is traffic is not route able. 

The second is the error "Destination Host Unreachable" which can come from pinging an address that is in the local network but there is no response from a device at that IP address.  The device is off or incapable of responding (firewall?).  

In addition to that you have a mix of Private addresses and kumc.edu DNS names (meaning public addresses?).  How is that possible since you shouldn't be able to route Private addresses and Private addresses should not be used in kumc.edu DNS name space.

Describe the physical connections (routers) and the actual IP addressing scheme for better diagnosis.

---

### Post by grandrigo on 2013-12-05
> **bab1 said:**
> 
The first is the error:  No route to host.  This suggests that the two devices are not on the same network and there is either no gateway configured on the host trying to ssh or there is no route defined on that host.  Are both hosts part of the same network?  If not you have a problem as the 10.0.0.0 /8 network is traffic is not route able. 


Yes they are part of the same network, all three devices are part of the same network. They are even connected in the same hook and not too long ago they were communicating with each other. 

> **bab1 said:**
> 
The second is the error "Destination Host Unreachable" which can come from pinging an address that is in the local network but there is no response from a device at that IP address.  The device is off or incapable of responding (firewall?).  

 
How can I check a firewall in Linux1?

> **bab1 said:**
> 
In addition to that you have a mix of Private addresses and XXX DNS names (meaning public addresses?).  How is that possible since you shouldn't be able to route Private addresses and Private addresses should not be used in XXX DNS name space.

I am sorry but I've tried changing the names of my actual computers to Linux1 and Linux2 for privacy issues. I would appreciate if you remove the domain name from your post, please :).  Everything is connected in the same XXX private network. 


> **bab1 said:**
>  Describe the physical connections (routers) and the actual IP addressing scheme for better diagnosis.
As far as I can tell you all these connections are part of the same routing cables in the office space.  Physically there are connected through a ethernet port to the wall. 

I know it's bizarre and the outputs makes you think they are in a different domain but how can Linux1 can communicate with any other machine in the network and LiveDuo as well but the communication between both is not working ???
As far as I know there is no firewall in Linux1

---

### Post by bab1 on 2013-12-05
> **grandrigo said:**
> Yes they are part of the same network, all three devices are part of the same network. They are even connected in the same hook and not too long ago they were communicating with each other. 


 
How can I check a firewall in Linux1?


I am sorry but I've tried changing the names of my actual computers to Linux1 and Linux2 for privacy issues. I would appreciate if you remove the domain name from your post, please :).  Everything is connected in the same XXX private network. 



As far as I can tell you all these connections are part of the same routing cables in the office space.  Physically there are connected through a ethernet port to the wall. 

I know it's bizarre and the outputs makes you think they are in a different domain but how can Linux1 can communicate with any other machine in the network and LiveDuo as well but the communication between both is not working ???
As far as I know there is no firewall in Linux1

So what you are saying is that you are using campus wiring to handle your personal private network.

---

### Post by grandrigo on 2013-12-05
Well...I work in a small imaging lab and we have our own private computers that we work on. IT do not support Linux (most likely they don't know much about it). I am the person with better networking knowledge in the lab and yes we try to stay away from them. I don't see a reason why asking for help to get a problem solved is an issue.

---

### Post by bab1 on 2013-12-05
> **grandrigo said:**
> Well...I work in a small imaging lab and we have our own private computers that we work on. IT do not support Linux (most likely they don't know much about it). I am the person with better networking knowledge in the lab and yes we try to stay away from them. I don't see a reason why asking for help to get a problem solved is an issue.

The infrastructure is owned and managed by the university.  In the university that I worked for we closed ports with unauthorized hardware attached.  No private addresses should be used with legitimate DNS domains. ```
NetRange:       10.0.0.0 - 10.255.255.255
CIDR:           10.0.0.0/8
OriginAS:       
NetName:        PRIVATE-ADDRESS-ABLK-RFC1918-IANA-RESERVED
NetHandle:      NET-10-0-0-0-1
Parent:         
NetType:        IANA Special Use
Comment:        These addresses are in use by many millions of independently operated networks, which might be as small as a single computer connected to a home gateway, and are automatically configured in hundreds of millions of devices.  They are only intended for use within a private context  and traffic that needs to cross the Internet will need to use a different, unique address.

```

---

### Post by The Cog on 2013-12-06
Firstly, it is very common to use network 10.* inside private networks, and in fact is the recommended way to do things. No problems there, and it would be irresponsible to use public addresses everywhere. Since the 10.* addresses are private, they are not reachable via the internet so there's no problem letting those be seen in the forums.

The networking config on the two Linux boxes is consistent and they both think they are on the same /24 subnet. That looks normal to me.

I can think of three possible explanations at the moment:
1: Firewall rules in one of the PCs that you're not aware of. Should be easy to check.
2: Network configuration that you're not aware of - firewall, access-list, closed user group etc.
3: There is another PC somewhere on the network with the same MAC or IP address as linux1. That could be hard to find.

First, let's check the firewall configuration. For linuix1 and linux2 use this command which prints the current firewall rules. If you can find an equivalent command on the LiveDuo that might be very useful (must run as root though):
```
sudo iptables-save -c
```

For checking the network configuration, you can perhaps talk to IT. Don't mention SSH, that should work once ping works so concentrate just on pinging. 
Swapping the ports that linux1 and linux2 are connected to might shed some light, but it may take several minutes (20 maybe) for the network to realise that they have moved so that won't be an option if the PCs are in constant use. 
Again, my next step would be to take a network trace. Running this command on both linux machines at the same time and then trying to ping LiveDuo from linux1 fora  couple of seconds with the traces running may help shed some light. If you can also run tcpdump on the liveduo the the same time, that would be even better:
```
sudo tcpdump -npe arp or icmp
```
Then immediately after that, do this on linux1:
```
arp -a
```

---

### Post by bab1 on 2013-12-06
> **The Cog said:**
> Firstly, it is very common to use network 10.* inside private networks, and in fact is the recommended way to do things. No problems there, and it would be irresponsible to use public addresses everywhere. Since the 10.* addresses are private, they are not reachable via the internet so there's no problem letting those be seen in the forums.

With one caveat,  You should use your own the infrastructure.  The OP doesn't.  The university that he/she works for does.  My best guess is that there are ACL' s for all ports to insure that users don't create such rogue networks.

---

### Post by The Cog on 2013-12-06
> You should use your own the infrastructure. The OP doesn't.
Where do you get that idea from?

---

### Post by bab1 on 2013-12-06
> **The Cog said:**
> Where do you get that idea from?

From the post you altered.   ;-)

---

### Post by grandrigo on 2013-12-06
Thanks for your help TheCog



For [COLOR=#000000][FONT=Ubuntu Mono]sudo iptables-save -c [/FONT][/COLOR]I got no output in Linux1 or Linux2.

_In Linux1_, I executed the tcpdump command and arp-a...later I also ping to LiveDuo while tcpdump was running, here is what I got:

For [COLOR=#000000][FONT=Ubuntu Mono]sudo tcpdump -npe arp or icmp[/FONT][/COLOR]


```
sudo tcpdump -npe arp or icmptcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
11:43:07.034765 00:1d:97:19:02:d9 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.8, length 46
11:43:08.623167 08:2e:5f:bc:20:b5 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (01:19:03:05:01:02) tell 10.50.4.16, length 46
11:43:09.089845 00:e0:db:10:e8:6f > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.107 (ff:ff:ff:ff:ff:ff) tell 10.50.4.107, length 46
11:43:10.091355 00:e0:db:10:e8:6f > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.107 (ff:ff:ff:ff:ff:ff) tell 10.50.4.107, length 46
11:43:11.550402 3c:07:54:7e:03:cf > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 tell 10.50.4.18, length 46
11:43:12.053241 00:1d:97:19:02:d7 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.10, length 46
11:43:14.068328 a0:b3:cc:fa:2c:e7 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.97 tell 10.50.4.17, length 46
11:43:14.068667 00:21:70:40:72:12 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.17 tell 10.50.4.97, length 46
11:43:15.571425 00:23:24:33:9a:88 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 tell 10.50.4.83, length 46
11:43:17.991058 00:1d:97:19:02:d6 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.9, length 46
11:43:18.718228 10:1f:74:fb:24:00 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 tell 10.50.4.27, length 46
11:43:18.733679 00:e0:db:11:24:6f > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.76 (ff:ff:ff:ff:ff:ff) tell 10.50.4.76, length 46
11:43:19.735153 00:e0:db:11:24:6f > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.76 (ff:ff:ff:ff:ff:ff) tell 10.50.4.76, length 46
11:43:20.341197 00:21:70:40:72:12 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.29 tell 10.50.4.97, length 46
11:43:21.699022 00:24:e8:39:42:6e > 70:ca:9b:18:63:45, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.1 tell 10.50.4.59, length 28
11:43:21.701044 70:ca:9b:18:63:45 > 00:24:e8:39:42:6e, ethertype ARP (0x0806), length 60: Reply 10.50.4.1 is-at 70:ca:9b:18:63:45, length 46
11:43:23.077889 00:24:e8:fd:40:de > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.29 tell 10.50.4.30, length 46
11:43:24.582669 00:1b:4f:6d:22:f2 > ff:ff:ff:ff:ff:ff, ethertype 802.1Q (0x8100), length 64: vlan 121, p 0, ethertype ARP, Request who-has 10.50.121.6 (22:f2:81:00:a0:79) tell 10.50.121.16, length 46
11:43:24.589274 00:1b:4f:6d:00:f8 > ff:ff:ff:ff:ff:ff, ethertype 802.1Q (0x8100), length 64: vlan 121, p 0, ethertype ARP, Request who-has 10.50.121.16 (00:f8:81:00:a0:79) tell 10.50.121.6, length 46
11:43:27.574101 00:13:72:ad:80:71 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.18 tell 10.50.4.57, length 46
11:43:27.604290 00:90:a9:bd:e6:12 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.18 tell 10.50.4.43, length 46
11:43:27.647259 00:25:64:38:8d:88 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.18 tell 10.50.4.5, length 46
11:43:27.821751 00:1d:97:19:02:d9 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.8, length 46
11:43:30.026060 9c:8e:99:dc:94:a8 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 tell 10.50.4.90, length 46
11:43:32.859135 00:1d:97:19:02:d7 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.10, length 46
11:43:37.231694 00:e0:db:10:e8:02 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.66 (ff:ff:ff:ff:ff:ff) tell 10.50.4.66, length 46
11:43:37.438616 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has **10.50.4.43** tell 10.50.4.59, length 28
11:43:38.233228 00:e0:db:10:e8:02 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.66 (ff:ff:ff:ff:ff:ff) tell 10.50.4.66, length 46
11:43:38.434965 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:39.435029 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:40.453221 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:40.760059 00:e0:db:10:6c:bf > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.69 (ff:ff:ff:ff:ff:ff) tell 10.50.4.69, length 46
11:43:41.176719 00:1d:97:19:02:d7 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.10, length 46
11:43:41.451025 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:41.761574 00:e0:db:10:6c:bf > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.69 (ff:ff:ff:ff:ff:ff) tell 10.50.4.69, length 46
11:43:42.094405 08:2e:5f:bc:20:b5 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (01:3c:16:00:08:c3) tell 10.50.4.16, length 46
11:43:42.451026 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:43.469204 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:44.264760 00:1d:97:19:02:d6 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.9, length 46
11:43:44.467028 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:45.467027 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
11:43:45.507023 00:24:e8:39:42:6e > 70:ca:9b:18:63:45, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.1 tell 10.50.4.59, length 28
11:43:45.508413 70:ca:9b:18:63:45 > 00:24:e8:39:42:6e, ethertype ARP (0x0806), length 60: Reply 10.50.4.1 is-at 70:ca:9b:18:63:45, length 46
11:43:46.190005 10:1f:74:fb:24:00 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 tell 10.50.4.27, length 46
11:43:46.485246 00:24:e8:39:42:6e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.43 tell 10.50.4.59, length 28
^C
45 packets captured
45 packets received by filter
0 packets dropped by kernel

```
[U]Output for arp-a in Linux1:
[/U]```
~$ sudo arp -aLinux2.<some_domain> (10.50.4.5) at 00:25:64:38:8d:88 [ether] on eth0
? (10.50.4.1) at 70:ca:9b:18:63:45 [ether] on eth0
<other_Hostname>.<some_domain> (10.50.4.82) at 3c:07:54:7e:06:1e [ether] on eth0
LiveDuo.<some_domain> (10.50.4.43) at 00:90:a9:bd:e6:12 [ether] on eth0
<other_Hostname>.<some_domain> (10.50.4.45) at 00:13:72:0b:e5:54 [ether] on eth0

```



**_Linux2_:**
Same approach in Linux 2

(the tcpdump command0
.
.
.
```
11:47:37.669979 00:25:64:38:8d:88 > 9c:8e:99:de:8b:ab, ethertype ARP (0x0806), length 42: Reply 10.50.4.5 is-at 00:25:64:38:8d:88, length 28
11:47:37.698811 f4:ce:46:14:22:15 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.50, length 46
11:47:37.721238 00:1a:a0:42:ab:cc > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.114, length 46
11:47:37.749267 18:a9:05:b2:86:72 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.78, length 46
11:47:37.755088 00:23:24:00:bb:3b > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.14, length 46
11:47:37.773299 74:46:a0:96:c9:9c > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.112, length 46
11:47:37.790462 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.115 tell 10.50.4.105, length 46
11:47:37.790626 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.92 tell 10.50.4.105, length 46
11:47:37.809139 18:a9:05:b3:04:5f > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.33, length 46
11:47:37.813107 3c:d9:2b:5c:d9:23 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.22, length 46
11:47:37.824252 00:21:9b:6e:e3:52 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.80, length 46
11:47:37.839705 00:1a:a0:7a:46:42 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.99, length 46
11:47:37.850435 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.53 tell 10.50.4.105, length 46
11:47:37.920436 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.21 tell 10.50.4.105, length 46
11:47:37.950350 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.116 tell 10.50.4.105, length 46
11:47:38.000434 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.81 tell 10.50.4.105, length 46
11:47:38.050576 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.106 tell 10.50.4.105, length 46
11:47:38.120357 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.90 tell 10.50.4.105, length 46
11:47:38.160343 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.123 tell 10.50.4.105, length 46
11:47:38.420426 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.112 tell 10.50.4.105, length 46
11:47:38.430228 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.15 tell 10.50.4.105, length 46
11:47:38.530376 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.42 tell 10.50.4.105, length 46
11:47:38.550260 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.73 tell 10.50.4.105, length 46
11:47:38.620416 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.78 tell 10.50.4.105, length 46
11:47:38.660416 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.27 tell 10.50.4.105, length 46
11:47:38.690414 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.7 tell 10.50.4.105, length 46
11:47:38.700362 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.99 tell 10.50.4.105, length 46
11:47:38.700366 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.28 tell 10.50.4.105, length 46
11:47:38.750322 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.44 tell 10.50.4.105, length 46
11:47:38.820429 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.38 tell 10.50.4.105, length 46
11:47:38.852196 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.120 tell 10.50.4.105, length 46
11:47:38.931003 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.117 tell 10.50.4.105, length 46
11:47:38.950413 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.110 tell 10.50.4.105, length 46
11:47:38.980700 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.114 tell 10.50.4.105, length 46
11:47:39.060421 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.104 tell 10.50.4.105, length 46
11:47:39.130433 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.71 tell 10.50.4.105, length 46
11:47:39.140613 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.54 tell 10.50.4.105, length 46
11:47:39.250403 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.17 tell 10.50.4.105, length 46
11:47:39.300517 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.24 tell 10.50.4.105, length 46
11:47:39.300667 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.14 tell 10.50.4.105, length 46
11:47:39.310350 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.23 tell 10.50.4.105, length 46
11:47:39.420858 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.50 tell 10.50.4.105, length 46
11:47:39.500370 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.16 tell 10.50.4.105, length 46
11:47:39.614724 00:25:64:38:8d:88 > 70:ca:9b:18:63:45, ethertype IPv4 (0x0800), length 144: 10.50.4.5 > 10.2.106.7: ICMP 10.50.4.5 udp port 6779 unreachable, length 110
11:47:39.650361 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.40 tell 10.50.4.105, length 46
11:47:39.780500 00:1d:97:19:02:d6 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.9, length 46
11:47:39.860412 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.80 tell 10.50.4.105, length 46
11:47:40.172116 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.125 tell 10.50.4.105, length 46
11:47:40.230477 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.124 tell 10.50.4.105, length 46
11:47:40.480700 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.33 tell 10.50.4.105, length 46
11:47:40.570547 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.22 tell 10.50.4.105, length 46
11:47:42.380846 00:1d:97:19:02:d9 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.8, length 46
11:47:43.090683 00:e0:db:10:e8:02 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.66 (ff:ff:ff:ff:ff:ff) tell 10.50.4.66, length 46
11:47:43.926142 00:90:a9:bd:e6:12 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.105 tell 10.50.4.43, length 46
11:47:44.092184 00:e0:db:10:e8:02 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.66 (ff:ff:ff:ff:ff:ff) tell 10.50.4.66, length 46
11:47:44.573622 00:1d:97:19:02:d7 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.10, length 46
11:47:44.629759 00:25:64:38:8d:88 > 70:ca:9b:18:63:45, ethertype ARP (0x0806), length 42: Request who-has 10.50.4.1 tell 10.50.4.5, length 28
11:47:44.631943 70:ca:9b:18:63:45 > 00:25:64:38:8d:88, ethertype ARP (0x0806), length 60: Reply 10.50.4.1 is-at 70:ca:9b:18:63:45, length 46
11:47:46.192275 9c:8e:99:de:8b:ab > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.43 tell 10.50.4.105, length 46
11:47:46.621488 08:2e:5f:bc:20:b5 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (01:19:03:05:01:02) tell 10.50.4.16, length 46
11:47:46.623002 00:50:aa:27:cb:0c > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:fd:16:00:fa:01) tell 10.50.4.36, length 46
11:47:46.653348 00:e0:db:10:6c:bf > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.69 (ff:ff:ff:ff:ff:ff) tell 10.50.4.69, length 46
11:47:47.654830 00:e0:db:10:6c:bf > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.69 (ff:ff:ff:ff:ff:ff) tell 10.50.4.69, length 46
11:47:50.623228 00:1d:97:19:02:d9 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.8, length 46
11:47:52.391724 6c:3b:e5:14:88:17 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.97 tell 10.50.4.15, length 46
11:47:52.392286 00:21:70:40:72:12 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.15 tell 10.50.4.97, length 46
11:47:53.302874 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 1, length 64
11:47:53.303052 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 1, length 64
11:47:54.301870 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 2, length 64
11:47:54.302053 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 2, length 64
11:47:55.301777 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 3, length 64
11:47:55.301995 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 3, length 64
11:47:56.301782 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 4, length 64
11:47:56.301951 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 4, length 64
11:47:57.301777 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 5, length 64
11:47:57.301919 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 5, length 64
11:47:58.301769 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 6, length 64
11:47:58.301944 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 6, length 64
11:47:59.085766 00:1b:4f:6d:00:74 > ff:ff:ff:ff:ff:ff, ethertype 802.1Q (0x8100), length 64: vlan 121, p 0, ethertype ARP, Request who-has 10.50.121.1 (00:74:81:00:a0:79) tell 10.50.121.8, length 46
11:47:59.301771 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 7, length 64
11:47:59.301948 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 7, length 64
11:47:59.603920 9c:8e:99:de:8b:ab > 00:25:64:38:8d:88, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.5 (00:25:64:38:8d:88) tell 10.50.4.105, length 46
11:47:59.603929 00:25:64:38:8d:88 > 9c:8e:99:de:8b:ab, ethertype ARP (0x0806), length 42: Reply 10.50.4.5 is-at 00:25:64:38:8d:88, length 28
11:48:00.301771 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 8, length 64
11:48:00.301939 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 8, length 64
11:48:00.523894 00:1d:97:19:02:d6 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 10.50.4.1 (ff:ff:ff:ff:ff:ff) tell 10.50.4.9, length 46
11:48:01.301768 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 9, length 64
11:48:01.301984 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 9, length 64
11:48:02.301780 00:25:64:38:8d:88 > 00:90:a9:bd:e6:12, ethertype IPv4 (0x0800), length 98: 10.50.4.5 > 10.50.4.43: ICMP echo request, id 25337, seq 10, length 64
11:48:02.301952 00:90:a9:bd:e6:12 > 00:25:64:38:8d:88, ethertype IPv4 (0x0800), length 98: 10.50.4.43 > 10.50.4.5: ICMP echo reply, id 25337, seq 10, length 64
^C
154 packets captured
154 packets received by filter
0 packets dropped by kernel

```

[U]Output for arp-a:

[/U```
]~$ arp -a
<AnotherHostname>.<Some_domain> (10.50.4.82) at 3c:07:54:7e:06:1e [ether] on eth0
<AnotherHostname>.<Some_domain>  (10.50.4.4) at 00:23:24:08:0f:1f [ether] on eth0
LiveDuo.<some_Domain> (10.50.4.43) at 00:90:a9:bd:e6:12 [ether] on eth0
<AnotherHostname>.<Some_domain> (10.50.4.97) at 00:21:70:40:72:12 [ether] on eth0
<AnotherHostname>.<Some_domain>  (10.50.4.68) at 9c:8e:99:de:8c:0d [ether] on eth0
<AnotherHostname>.<Some_domain>  (10.50.4.29) at 10:9a:dd:43:25:8f [ether] on eth0
<AnotherHostname>.<Some_domain>  (10.50.4.105) at 9c:8e:99:de:8b:ab [ether] on eth0
Linux1.<some_domain> (10.50.4.59) at 00:24:e8:39:42:6e [ether] on eth0
<AnotherHostname>.<Some_domain> (10.50.4.18) at 3c:07:54:7e:03:cf [ether] on eth0


? (10.50.4.1) at 70:ca:9b:18:63:45 [ether] on eth0
```

---

### Post by grandrigo on 2013-12-06
I don't know how to execute tcpdump in the LiveDuo....the command is not installed on  it.

---

### Post by grandrigo on 2013-12-06
I don't know how to execute tcpdump in the LiveDuo....the command is not installed on  it. 

Also, I tracked the mount command  the other researcher typed when trying to mount LiveDuo. The problem appeared right after this happened....

Here is what he did:
#$ sudo mount.cifs //10.50.4.43/Public /mnt/cifs


Obviously is not mounted anymore (or at least I know) I used df -h to check for mount filesystems and the disk utility GUI

---

### Post by The Cog on 2013-12-06
> For sudo iptables-save -c I got no output in Linux1 or Linux2.
That's OK. It means the linux boxes don't have any firewall rules running. That rules out one possible cause.

Linux1 is correctly sending ARP requests for LiveDuo (10.50.4.43) but does not receive a reply. Without the reply it cannot tell which MAC address to send the pings to, so reports "No route to host" to the user. There is nothing wrong with linux1, the problem is in the network or in the LiveDuo box.

You can see from the tcpdump from linux2 that LiveDuo is there and responding to ping requests. I don't see an ARP request before the pings start, so linux2 already knows the MAC address by the time the pings start. Either because of something that happened before tcpdump started, or because it saw an ARP request ***from*** LiveDuo shortly before the pings started (at 11:47:43.9). 

Interestingly, both linux1 and linux2 list "(10.50.4.43) at 00:90:a9:bd:e6:12" in their arp tables when you enter "arp -a". I don't know how linux1 figured that out. Actually I meant to say to use arp -n but no matter.

You could try to manually make an ARP entry into linux1 for the LiveDuo with the following command:
```
sudo arp -s 10.50.4.43 00:90:a9:bd:e6:12
```
My guess is that whatever is preventing ARP from working would prevent the ping from working too, but it is a quick test to do.

Really at this stage, I think it is either the network or the LiveDuo. Since you say the mount.cifs command may have triggered the behaviour, I wonder if linux1 has been blacklisted by the liveduo for not giving the right authentication credentials for the mount.

I'm sorry but I don't think there is much more I can do. The problem is not with the Linux boxes. My guesses would be (in order of likelihood)
1: LiveDuo has blacklisted linux1 for some reason, maybe it didn't like that mount.cifs attempt.
2: Another PC on the network has the same IP address (or less likely, the same MAC address) as linux1
3: something I haven't thought of.
4: The network is filtering packets between LiveDuo and Linux1.

---

### Post by grandrigo on 2013-12-06
Thanks for your help. So I decided to restore to factory settings LiveDuo and the problem keeps existing. I'll talk to IT to see if they block the communication between both. If not, the next step will be to reformat Linux1 :/

---

### Post by The Cog on 2013-12-07
If you ever find out what the problem was, I'd be interested to know. Wishing you luck with it, and sorry I couldn't help more. I really don't think linux is the problem here. Before all the pain of installing, try a live CD and try the pings from there. If the live CD can't ping it, then I doubt whether reinstalling would fix the problem.

---

