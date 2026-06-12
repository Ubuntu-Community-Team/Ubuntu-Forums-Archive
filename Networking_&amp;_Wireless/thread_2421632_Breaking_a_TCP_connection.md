---
title: "Breaking a TCP connection"
date: 2019-06-25
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2019-06-25
is there a tool that i could use (via [FONT=courier new]sudo[/FONT]) that can force _drop_ a TCP connection (or SCTP session) based on knowing the 2 addresses and ports it is working on (that can be seen in [FONT=courier new]netstat[/FONT] or [FONT=courier new]tcpdump[/FONT])?

---

### Post by Doug S on 2019-06-26
You could use iptables to force a DROP:

```
sudo iptables -I INPUT 1 -s 100.101.102.103 -i enp4s0 -j DROP
```

And actually, I do this on my system often. If you have an existing iptables rules set, or an UFW generated iptables rule set, you will have to determine the correct place to put the rule. On my system, I usually do it as INPUT rule 26:

```
sudo iptables -I INPUT 26 -s 100.101.102.103 -i enp4s0 -j DROP
``` And note also, for attacks, in recent years they (China mainly) just switch to another IP address on the same sub-net, so I look up the sub-net mask and block the entire subnet:

```
sudo iptables -I INPUT 26 -s 45.114.8.0/22 -i enp4s0 -j DROP
```Of course, I also edit my master file so that the rules will be there after re-boots.

---

### Post by Skaperen on 2019-06-27
isn't that just a rule to drop packets and prevent traffic?  i have an existing connection that is already established that the peer is no longer sending anything on.  i do not want to signal or kill the local process as that will be ungraceful and lose data.  instead i wand to process to act as if the connect was closed.  also, the Linux box is just the router.  the process on the local end is on another box.  so i would need to send a TCP RST with the right sequence number.  but i recall reading, a couple years ago, about a program that could do this.

---

### Post by #&amp;thj^% on 2019-06-27
Would something like this be satisfactory?
Closing a socket in a running process is not impossible but it is difficult: [https://superuser.com/questions/127863/manually-closing-a-port-from-commandline/668155#668155](https://superuser.com/questions/127863/manually-closing-a-port-from-commandline/668155#668155)

---

### Post by The Cog on 2019-06-27
Yes, that rule just drops the packets. Better might be to use -j REJECT which actively closes the connection in response to a packet. I'm not sure now if it sends ICMP unreachable or whether it sends a RST though. And TCP connections that are idle with no keepalive would never discover that the path was no longer working, so wouldn't close.

Anyway, it probably won't work on an existing connections because most firewall rule sets have an early rule that allows existing connections through (permit ESTABLISHED). This saves every packet having to pass through all the filter tests. Only the initial connection setup goes through all the filter rules. So after adding the new rule you would also have to use the conntrack command to remove that connection from the connection tracking table.

There almost certainly are programs that can send a RST to a specified addr+port pair, but I don't know what they are. I suspect that you don't have to give a good sequence number in a RST packet, but haven't checked. ddg found this for me: [http://www.ubuntugeek.com/sendip-tool-to-send-arbitrary-ip-packets.html](http://www.ubuntugeek.com/sendip-tool-to-send-arbitrary-ip-packets.html)

---

### Post by Doug S on 2019-06-27
> **The Cog said:**
> Anyway, it probably won't work on an existing connections because most firewall rule sets have an early rule that allows existing connections through (permit ESTABLISHED). This saves every packet having to pass through all the filter tests. Only the initial connection setup goes through all the filter rules. So after adding the new rule you would also have to use the conntrack command to remove that connection from the connection tracking table.If you put the rule before the typical REALATED,ESTABLISHED rule, it'll drop any packets from the IP, regardless. Chains that are only traversed once for NEW connections are, for example the nat PREROUTING chain, but the INPUT chain is traversed for every packet that gets to the INPUT chain.

The connection tracking table only exists if you already have some itpbales rules that require it. Then yes, it is trivial to drop that existing connection.

EDIT: Oh, I see the OPs box is a router. Then it is likely that the nat PREROUTEING chain is being used.

---

### Post by kpatz on 2019-06-27
> **Skaperen said:**
> ...i do not want to signal or kill the local process as that will be ungraceful and lose data....What is the local process?  Many will close gracefully on a SIGTERM signal, and disconnect the connection cleanly.  SIGHUP may also close cleanly depending on the application.  Of course using SIGKILL (-9) will force an unclean shutdown.

---

### Post by The Cog on 2019-06-27
Good point. Just make sure the rule is above the RELATED rule. And on looking back, you used -I not -A. My bad.

---

### Post by Skaperen on 2019-06-28
right, this is the router i am doing this from.  and there are no packets being sent in either direction.

---

### Post by Doug S on 2019-06-28
> **Skaperen said:**
> i have an existing connection that is already established that the peer is no longer sending anything on.  i do not want to signal or kill the local process as that will be ungraceful and lose data.  instead i wand to process to act as if the connect was closed.  also, the Linux box is just the router.  the process on the local end is on another box.  so i would need to send a TCP RST with the right sequence number.  but i recall reading, a couple years ago, about a program that could do this.Already installed on one of my computers is "hping3", which can send almost what you want, but I don't know the proper sequence number to provide:

```
$ sudo hping3 --count 1 --spoof 192.168.111.1 --baseport 51086 --destport 22 --rst 192.168.111.120
```

But it has no effect:

```
doug@s17:~$ sudo tcpdump -n -tttt -i ens5 not host 192.168.111.101
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ens5, link-type EN10MB (Ethernet), capture size 262144 bytes
2019-06-28 11:59:18.775302 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [P.], seq 2280786151:2280786187, ack 1881387854, win 296, options [nop,nop,TS val 550886439 ecr 2632743252], length 36
2019-06-28 11:59:18.776225 IP 192.168.111.120.22 > 192.168.111.1.51086: Flags [P.], seq 1:69, ack 36, win 312, options [nop,nop,TS val 2632833224 ecr 550886439], length 68
2019-06-28 11:59:18.776462 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [.], ack 69, win 296, options [nop,nop,TS val 550886439 ecr 2632833224], length 0
2019-06-28 11:59:19.232814 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [P.], seq 36:72, ack 69, win 296, options [nop,nop,TS val 550886554 ecr 2632833224], length 36
2019-06-28 11:59:19.233147 IP 192.168.111.120.22 > 192.168.111.1.51086: Flags [P.], seq 69:105, ack 72, win 312, options [nop,nop,TS val 2632833681 ecr 550886554], length 36
2019-06-28 11:59:19.233377 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [.], ack 105, win 296, options [nop,nop,TS val 550886554 ecr 2632833681], length 0
2019-06-28 11:59:19.233392 IP 192.168.111.120.22 > 192.168.111.1.51086: Flags [P.], seq 105:173, ack 72, win 312, options [nop,nop,TS val 2632833681 ecr 550886554], length 68
2019-06-28 11:59:19.233604 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [.], ack 173, win 296, options [nop,nop,TS val 550886554 ecr 2632833681], length 0
[COLOR="#FF0000"]2019-06-28 11:59:33.652957 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [R], seq 1992732150, win 512, length 0[/COLOR]
2019-06-28 12:08:00.901149 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [P.], seq 2280786223:2280786259, ack 1881388026, win 296, options [nop,nop,TS val 551016971 ecr 2632833681], length 36
2019-06-28 12:08:00.902129 IP 192.168.111.120.22 > 192.168.111.1.51086: Flags [P.], seq 1:69, ack 36, win 312, options [nop,nop,TS val 2633355350 ecr 551016971], length 68
2019-06-28 12:08:00.902353 IP 192.168.111.1.51086 > 192.168.111.120.22: Flags [.], ack 69, win 296, options [nop,nop,TS val 551016971 ecr 2633355350], length 0

```
```
doug@DOUG-64:~$ sudo conntrack -L | grep "192\.168\.111\.120"
tcp      6 35853 ESTABLISHED src=192.168.111.1 dst=192.168.111.120 sport=51086 dport=22 src=192.168.111.120 dst=192.168.111.1 sport=22 dport=51086 [ASSURED] mark=0 use=1
conntrack v1.4.3 (conntrack-tools): 49 flow entries have been shown.
```

---

### Post by The Cog on 2019-06-28
I'm not sure that the conntrack entry will disappear straight away. It might retain the entry for a few minutes in case there are some straggler packets on the connection. I would want to check the end device with ss (or ask the application) to be sure.

And bear in mind that there is no response to a RST (it means "No such connection"). So if you spoof a RST to end A, then end A will close, but end B will never know (until it sends to end A and gets a RST back).

---

### Post by Doug S on 2019-06-28
> **The Cog said:**
> I'm not sure that the conntrack entry will disappear straight away. It might retain the entry for a few minutes in case there are some straggler packets on the connection. I would want to check the end device with ss (or ask the application) to be sure.

And bear in mind that there is no response to a RST (it means "No such connection"). So if you spoof a RST to end A, then end A will close, but end B will never know (until it sends to end A and gets a RST back).Agreed. I actually didn't expect the conntrack table entry to disappear, just showed it for completeness. And, also I showed that the connection was actually still working in my tcpdump capture, where we see some more packets several minutes after the [COLOR="#FF0000"]RED[/COLOR] highlighted RST packet

By the way, the test I wrote up was with a 3rd computer spoofing my gateway/router computer. However, later, I also did the test involving two computers only, with no spoofing. My thinking was just in case the different MAC address had something to do with it. I also tried setting the FIN flag instead of RST. I read somewhere that a proper sequence number isn't actually needed to close a connection, but I do not know if that reference was correct, nor could I make it work. @Skaperen's problem is interesting, but myself I have never seen a long lingering TCP connection in my Ubuntu server router connection tracking table. And for any lingering TCP connection in local clients, I wouldn't know for sure.

---

### Post by Skaperen on 2019-06-28
i found a program called [killcx]("http://killcx.sourceforge.net/") written in Perl that claims it can do this.  it finds out the sequence number by spoofing a SYN, first, then sending a RST with the sequence number.  now i need to figure out how to get these Perl modules it needs installed.  i do Python; Perl is a mystery to me.

---

### Post by Doug S on 2019-06-28
> **Skaperen said:**
> now i need to figure out how to get these Perl modules it needs installed.  i do Python; Perl is a mystery to me.How about this:

```
apt-get install libnetpacket-perl  libnet-pcap-perl libnet-rawip-perl
```Copy and pasted from [here]("https://stackoverflow.com/questions/33198881/close-established-tcp-connection-on-linux").

---

### Post by blekx on 2019-07-01
I'm not sure if you are still trying to get an answer for this, but you can use netstat to get the process id and then kill the process.
The netstat would look something like:

```
sudo netstat -nlpa | grep <IP address>
```

There could be several lines in the netstat output. The process ID will be listed in the far right column with the application name. Choose the one you want and then kill the process with:

```
sudo kill <process ID>
```

Bev.

---

### Post by Skaperen on 2019-07-02
> **kpatz said:**
> What is the local process?  Many will close gracefully on a SIGTERM signal, and disconnect the connection cleanly.  SIGHUP may also close cleanly depending on the application.  Of course using SIGKILL (-9) will force an unclean shutdown.

i don't want to take down the whole service, i just want the one connection to drop.  and i want to be able to do it from the router where i (no longer) see the traffic.

i want to automate this, too.

---

### Post by Skaperen on 2019-07-02
turns out there is a program (in Perl) that can do this at [http://killcx.sourceforge.net/](http://killcx.sourceforge.net/).  it sends a SYN to discover the sequence number then sends a RST.

---

