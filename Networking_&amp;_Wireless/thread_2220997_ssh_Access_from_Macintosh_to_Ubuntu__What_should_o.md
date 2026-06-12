---
title: "ssh Access from Macintosh to Ubuntu ? What should one do ?"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by xptional on 2014-04-30
[FONT=Verdana]I have a  Dell machine installed with ubuntu 10.04. I use it in my lab. It has wireless connection right now. I need to access this machine from home. At home I have macintosh. 

[/FONT]
[FONT=Verdana]On my ubuntu machine[/FONT]
[FONT=Verdana]```
ifconfig
```[/FONT]
> 
[FONT=Verdana]khan@ubuntu:~$ ifconfig[/FONT]
[FONT=Verdana]eth0      Link encap:Ethernet  HWaddr 00:21:9b:ee:6b:92  [/FONT]
[FONT=Verdana]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Verdana]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Verdana]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Verdana]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Verdana]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
[FONT=Verdana]          Interrupt:16 [/FONT]

[FONT=Verdana]lo        Link encap:Local Loopback  [/FONT]
[FONT=Verdana]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=Verdana]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=Verdana]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
[FONT=Verdana]          RX packets:82 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Verdana]          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Verdana]          collisions:0 txqueuelen:0 [/FONT]
[FONT=Verdana]          RX bytes:11439 (11.4 KB)  TX bytes:11439 (11.4 KB)[/FONT]

[FONT=Verdana]wlan0     Link encap:Ethernet  HWaddr 00:21:5d:c9:9a:34  [/FONT]
[FONT=Verdana]**inet addr:141.115.36.122**[/FONT][FONT=Verdana]  Bcast:141.115.36.255  Mask:255.255.255.0[/FONT]
[FONT=Verdana]          inet6 addr: fe80::221:5dff:fec9:9a34/64 Scope:Link[/FONT]
[FONT=Verdana]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Verdana]          RX packets:86833 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Verdana]          TX packets:54410 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Verdana]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Verdana]          RX bytes:114705252 (114.7 MB)  TX bytes:7241194 (7.2 MB)[/FONT]


[FONT=Verdana]There is nothing in hosts.allow and hosts.deny[/FONT]
[FONT=Verdana]```
khan@ubuntu:~$ cat /etc/hosts.allow 
```[/FONT]
> 
[FONT=Verdana]# /etc/hosts.allow: list of hosts that are allowed to access the system.[/FONT]
[FONT=Verdana]#                   See the manual pages hosts_access(5) and hosts_options(5).[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# Example:    ALL: LOCAL @some_netgroup[/FONT]
[FONT=Verdana]#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# If you're going to protect the portmapper use the name "portmap" for the[/FONT]
[FONT=Verdana]# daemon name. Remember that you can only use the keyword "ALL" and IP[/FONT]
[FONT=Verdana]# addresses (NOT host or domain names) for the portmapper, as well as for[/FONT]
[FONT=Verdana]# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)[/FONT]
[FONT=Verdana]# for further information.[/FONT]
[FONT=Verdana]#[/FONT]

[FONT=Verdana]```
khan@ubuntu:~$ cat /etc/hosts.deny 
```[/FONT]
> 
[FONT=Verdana]# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.[/FONT]
[FONT=Verdana]#                  See the manual pages hosts_access(5) and hosts_options(5).[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# Example:    ALL: some.host.name, .some.domain[/FONT]
[FONT=Verdana]#             ALL EXCEPT in.fingerd: other.host.name, .other.domain[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# If you're going to protect the portmapper use the name "portmap" for the[/FONT]
[FONT=Verdana]# daemon name. Remember that you can only use the keyword "ALL" and IP[/FONT]
[FONT=Verdana]# addresses (NOT host or domain names) for the portmapper, as well as for[/FONT]
[FONT=Verdana]# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)[/FONT]
[FONT=Verdana]# for further information.[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# The PARANOID wildcard matches any host whose name does not match its[/FONT]
[FONT=Verdana]# address.[/FONT]
[FONT=Verdana]#[/FONT]
[FONT=Verdana]# You may wish to enable this to ensure any programs that don't[/FONT]
[FONT=Verdana]# validate looked up hostnames still leave understandable logs. In past[/FONT]
[FONT=Verdana]# versions of Debian this has been the default.[/FONT]
[FONT=Verdana]# ALL: PARANOID[/FONT]


[FONT=Verdana]On macintosh machine at home, I did ping but did not work. I did ssh, did not work.[/FONT]

[FONT=Verdana]```
ping 141.115.36.122
```[/FONT]
[FONT=Verdana]> PING 141.115.36.122 (141.115.36.122): 56 data bytes[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 0[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 1[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 2[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 3[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 4[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 5[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 6[/FONT]
[FONT=Verdana]Request timeout for icmp_seq 7[/FONT]
[FONT=Verdana]^Z[/FONT]

[FONT=Verdana]When I do as bleow:[/FONT]
[FONT=Verdana]```
ssh khan@141.115.36.122
```[/FONT]
[FONT=Verdana]I get the following messages after awhile:[/FONT]
[FONT=Verdana]> ssh: connect to host 141.115.36.122 port 22: Operation timed out[/FONT]> 


[FONT=Verdana]All above things, I learned by googling. Even I modified hosts.allow file by going into root permisions on ubuntu machine, as such, ALL:ALL, but did not work. etc.[/FONT]

Any how, I can access lab servers from home by [ssh username@servername]. But now I want to access my personal ubuntu machine placed at lab.

[FONT=Verdana]What should I need on Macintosh machine or Ubuntu machine. [/FONT]
[FONT=Verdana]Please help me step by step. Its is my first time to connect remotely and i will be much happy to do that. [/FONT]
[FONT=Verdana]Thanks in advance![/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by Lars Noodén on 2014-04-30
On the lab machine, 141.115.36.122, can you ssh to yourself?  

```

ping -c 5 -w 1 141.115.36.122
ssh localhost
ssh 141.115.36.122 

```

If all of those work, then we can look more at connectivity.  Not being able to ping from outside indicates a problem.  You can get to other machines in the same lab from outside?

---

### Post by ian-weisser on 2014-04-30
Does your Ubuntu server respond to a ping from another machine on your LAN?
Can you ssh into your Ubuntu server from another machine on your LAN?

The answers to those questions will tell you if the issue is caused a setting or package on the Ubuntu machine, or if the issue is caused by your network's administrator.

---

### Post by xptional on 2014-04-30
In response to Mr. [**Lars Noodén**]("http://ubuntuforums.org/member.php?u=168643")[COLOR=#000000][/COLOR] 
Ping on lab machine (ubuntu)
> ping -c 5 -w 1 141.115.36.122
PING 141.115.36.122 (141.115.36.122) 56(84) bytes of data.
64 bytes from 141.115.36.122: icmp_seq=1 ttl=64 time=0.055 ms
64 bytes from 141.115.36.122: icmp_seq=2 ttl=64 time=0.042 ms


--- 141.115.36.122 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.042/0.048/0.055/0.009 ms


> ssh localhost
khan@localhost's password: 
Linux khan 2.6.32-58-generic #120-Ubuntu SMP Tue Apr 1 17:56:07 UTC 2014 i686 GNU/Linux
Ubuntu 10.04.4 LTS


Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


Last login: Wed Apr 30 15:10:49 2014 from localhost


> ssh 141.115.36.122
The authenticity of host '141.115.36.122 (141.115.36.122)' can't be established.
RSA key fingerprint is af:92:d6:45:58:1c:5e:6f:e1:c6:aa:a8:c8:3e:33:9d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '141.115.36.122' (RSA) to the list of known hosts.
khan@141.115.36.122's password: 
Linux khan 2.6.32-58-generic #120-Ubuntu SMP Tue Apr 1 17:56:07 UTC 2014 i686 GNU/Linux
Ubuntu 10.04.4 LTS


Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


Last login: Wed Apr 30 15:14:56 2014 from localhost


The password entry is of my personal lab machine(ubuntu). It is not password of wireless network of lab.

---

### Post by xptional on 2014-04-30
> **ian-weisser said:**
> Does your Ubuntu server respond to a ping from another machine on your LAN?
Can you ssh into your Ubuntu server from another machine on your LAN?

The answers to those questions will tell you if the issue is caused a setting or package on the Ubuntu machine, or if the issue is caused by your network's administrator.

If I connect my Macintosh Machine on the same wireless network of lab,  ( login n passwd are same to access this network either on macintosh or ubuntu, right now I dont have access to any other machine with different login and passwd )
Then the following:
> ping 141.115.36.122PING 141.115.36.122 (141.115.36.122): 56 data bytes
ping: sendto: No route to host
ping: sendto: Host is down
Request timeout for icmp_seq 0
ping: sendto: Host is down
Request timeout for icmp_seq 1
ping: sendto: Host is down
Request timeout for icmp_seq 2
ping: sendto: Host is down
Request timeout for icmp_seq 3
ping: sendto: Host is down
Request timeout for icmp_seq 4
ping: sendto: Host is down
Request timeout for icmp_seq 5
ping: sendto: Host is down
Request timeout for icmp_seq 6
ping: sendto: Host is down
Request timeout for icmp_seq 7
.
.
.


If I do ssh on macintosh connect to same wireless network,
> MacBook:~ KHAN$ ssh khan@141.115.36.122ssh: connect to host 141.115.36.122 port 22: Operation timed out


For your information Please, This lab network offcourse utilise proxy settings. The http proxy, secure http proxy, ftp proxy, sockts host : all with same port number. 

Looking forward for your cooperation. Thanks!

---

### Post by ian-weisser on 2014-04-30
Okay, so your Ubuntu system seems capable of making a connection.
Can it ping the mac?

Are you sure that both machines are connected to the same wireless network that you expect? "No route to host" is a specific error meaning that the machine you're looking for cannot be located on the network at all (instead of locatable but rejecting connections). If you have access to the router, do both machines show up?

---

### Post by Ubi_one_2014 on 2014-04-30
&#8203;u need to open port 22 in firewall of linux, and in the router of your lab


appologies for doing it, but i did an nmap scan to the ip 141.115.36.122 and no open ports where discovered[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by xptional on 2014-05-02
It was not accessible because the machine was not in lab. 
Port 22 of my Ubuntu machine is open. 
```
 nmap -A 127.0.0.1
```
> Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2014-05-02 11:16 CESTInteresting ports on localhost.localdomain (127.0.0.1):
Not shown: 998 closed ports
**PORT    STATE SERVICE VERSION**
[SIZE=4]**22/tcp  open  ssh     OpenSSH 5.3p1 Debian 3ubuntu7.1 (protocol 2.0)**[/SIZE]
|  ssh-hostkey: 1024 01:47:e4:2a:80:a7:4a:71:06:18:11:46:d9:d7:57:5d (DSA)
|_ 2048 af:92:d6:45:58:1c:5e:6f:e1:c6:aa:a8:c8:3e:33:9d (RSA)
631/tcp open  ipp     CUPS 1.4
Service Info: OS: Linux


Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 7.30 seconds


When I ping my machine some other machine placed in my lab that machine has wired connection. Then it works as follows:
> [COLOR=#262B33][FONT=monospace]PING 141.115.36.122 (141.115.36.122) 56(84) bytes of data.[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=1 ttl=63 time=0.999 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=2 ttl=63 time=0.716 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=3 ttl=63 time=0.907 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=4 ttl=63 time=0.719 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=5 ttl=63 time=0.686 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=6 ttl=63 time=1.86 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=7 ttl=63 time=0.925 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=8 ttl=63 time=0.616 ms[/FONT][/COLOR]
[COLOR=#262B33][FONT=monospace]64 bytes from 141.115.36.122: icmp_seq=9 ttl=63 time=0.693 ms[/FONT][/COLOR]

When I ping my Macintosh machine from Ubuntu machine both placed on the same wireless network of the lab.
then
> ping 141.115.36.63PING 141.115.36.63 (141.115.36.63) 56(84) bytes of data.
From 141.115.36.122 icmp_seq=1 Destination Host Unreachable
From 141.115.36.122 icmp_seq=2 Destination Host Unreachable
From 141.115.36.122 icmp_seq=3 Destination Host Unreachable
From 141.115.36.122 icmp_seq=4 Destination Host Unreachable
From 141.115.36.122 icmp_seq=5 Destination Host Unreachable
From 141.115.36.122 icmp_seq=6 Destination Host Unreachable
From 141.115.36.122 icmp_seq=7 Destination Host Unreachable
From 141.115.36.122 icmp_seq=8 Destination Host Unreachable
From 141.115.36.122 icmp_seq=9 Destination Host Unreachable
From 141.115.36.122 icmp_seq=10 Destination Host Unreachable
From 141.115.36.122 icmp_seq=11 Destination Host Unreachable
From 141.115.36.122 icmp_seq=12 Destination Host Unreachable
From 141.115.36.122 icmp_seq=13 Destination Host Unreachable
.
.
.

Please help ! Thanks

When I ping my Ubuntu machine from a macintosh machine both placed on the same wireless network. Then
> ping 141.115.36.122

PING 141.115.36.122 (141.115.36.122): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3
ping: sendto: No route to host
Request timeout for icmp_seq 4
ping: sendto: Host is down
Request timeout for icmp_seq 5
ping: sendto: Host is down
Request timeout for icmp_seq 6
ping: sendto: Host is down
Request timeout for icmp_seq 7
ping: sendto: Host is down
Request timeout for icmp_seq 8
ping: sendto: Host is down
Request timeout for icmp_seq 9
.
.


---

### Post by bapoumba on 2014-05-02
Is the firewall on the Mac allowing such connections or pings ?

---

### Post by xptional on 2014-05-02
I don't know, how to check firewall on the Mac ? Is it the problem of firewall or else, don't know. 
Please guide me. Thanks you !

---

### Post by bapoumba on 2014-05-02
> **xptional said:**
> I don't know, how to check firewall on the Mac ? Is it the problem of firewall or else, don't know. 
Please guide me. Thanks you !

This is just for the test that ian-weisser requested. I usually keep all incoming connections blocked. System Preferences > Security & Privacy > Firewall Tab.

---

### Post by Lars Noodén on 2014-05-02
> **xptional said:**
> I don't know, how to check firewall on the Mac ? Is it the problem of firewall or else, don't know. 
Please guide me. Thanks you !

By the way, nmap can only provide useful results if used from a second machine.  If used from the same machine it is scanning, all traffic will go via lo and that is usually unfiltered.  

Can you connect with ssh from a wired machine at all when your machine is on the wireless network?  Also, when your machine is on the wireless network, it probably has a different ip than when it is on a wired connection.  Can you double check to make sure that you have the current ip number?  How is that ip number assigned?  DHCP?

(Checking the firewall on the mac is probably 'sudo pfctl -sr' but that is probably not relevant to debugging, unless you changed it, it should allow outgoing connections.)

---

### Post by Ubi_one_2014 on 2014-05-02
@ XPtional

regardless where u are, when you want access through ssh, port 22 needs to be opened in your firewall and router on the ubuntu 10.04 pc, period!

---

### Post by theDaveTheRave on 2014-05-06
Hi all

I'm not sure if I'm being overly soppy but could the op please confirm some things for us.

You say that you can SSH to the works servers. The question that comes to my mind is once you are SSH'd to there, can you ping your Ubuntu terminal ? if not, then you aren't going to be able to ping it from outside (correct me if I'm wrong), or connect to it via SSH.

If you can ping it, you should be able to SSH to it, from the server.

So you'll be SSHing to your personal workstation from your logon to the server (I know it sounds complicated ;) ).

If you can do this, then you only have one problem to solve, and that is how to get the 'public' IP address of your workstation.

I expect that your Ubuntu terminal gets its wireless IP address from the server. All this is confused as this is a local only IP (as can be seen from the network mask), or at least I assume it is!
```

wlan0 Link encap:Ethernet HWaddr 00:21:5d:c9:9a:34
inet addr:141.115.36.122 Bcast:141.115.36.255 Mask:255.255.255.0

```

For instance if I navigate to [http://www.whatsmyip.org/]("http://www.whatsmyip.org/") I get an ip address of
```

85.170.91.211

```

However this is the IP of the server, and every terminal where I am will have the same public IP (it is the same on my mobile phone, tablet, desktop etc etc etc....)

So obviously we know that the IP address of the server that you SSH into is the same as it's public IP (or you wouldn't be able to ping it!).

So the OP needs to confirm that the IP of his Ubuntu terminal is unique.

I know that when I used to SSH to a server at work, or even use wake on lan on it, I needed to use the following
```

[public IP address of the server]:[port]:[local Ip or name of terminal to wake up]

```

You may need to do something similar to effectively ssh to your Ubuntu terminal.

However I also notice that your Ubuntu terminal has an IP6 address:
```

inet6 addr: fe80::221:5dff:fec9:9a34/64

```

Have a look here [http://www.cyberciti.biz/faq/howto-test-ipv6-network-with-ping6-command/ ]("http://www.cyberciti.biz/faq/howto-test-ipv6-network-with-ping6-command/") to see if you are set for using ipv6 from your home ISP (mine isn't using ipv6, so I can't ping your Ubuntu terminal).
I assume that if your ISP is on ipv6 you can ssh directly using that address ?

hope this gives some further investigations for you.

David.

ps: in brief just so you don't need to re-read all the stuff above again.

Visit [http://www.whatsmyip.org/]("http://www.whatsmyip.org/") from your Ubuntu terminal, and any other terminal at your work, if they give the same IP address, you unlikely to be able to SSH directly to your Ubuntu terminal.

SSH to your works server (as you allready can), check you can ping your Ubuntu terminal (141.115.36.122) whilst SSH'd to the server.
If you can (highly likely) try to SSH to your Ubuntu terminal from the Server connection.
If you can't ping.... I don't know what else to try? it maybe that your network admin has hidden any internal systems to improve security (it may be you need to log into another gateway terminal first), or your Ubuntu terminal refuses ping requests (so you could try to SSH anyhow).

hope that helps...

D

---

