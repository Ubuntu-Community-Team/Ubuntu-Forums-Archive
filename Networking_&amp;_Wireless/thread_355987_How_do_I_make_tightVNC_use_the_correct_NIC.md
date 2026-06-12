---
title: "How do I make tightVNC use the correct NIC?"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by d.j.schroeder on 2007-02-07
I don't know that this is directly an Ubuntu question, but the people on this forum are more helpful and knowledgeable than anywhere else I've found.  So here it goes:

_The background_
I have two networks, one with IP addresses that look like 192.168.100.x and one with IP addresses that look like 192.168.0.x.  I have a machine running 6.06LTS on the 192.168.100.x network.  I have another machine running Windows XP that normally uses the 192.168.0.x network, but has two NIC's and could be connected to either.  The reason I am asking this first instead of doing it is that it will require a substantial amount of time and effort to physically connect the XP machine to the other network.

_The question_
I want to be able connect the XP machine to the network the Ubuntu machine is on using it's other NIC and then use tightVNC (or other VNC software) to connect to the Ubuntu machine.  Is that possible?  If so, how do I get tightVNC to use the correct NIC?  Is specifying the correct address for the Ubuntu machine enough?

Thanks in advance for taking the time to read and answer if you can.

---

### Post by d.j.schroeder on 2007-02-08
Surely someone knows the answer to this...

Bump

---

### Post by d.j.schroeder on 2007-02-10
Well, I was hoping to get an answer to this before the drills and pipe benders had to come out, but I didn't.  So, I connected everything and now that I've done it I'll go ahead and answer my own question.

It is possible as long as the networks have different addresses like what I had stated in my earlier post.  TightVNC connects fine to the Ubuntu machine if I just use its local IP address.

Hopefully, this information will be useful to someone else.

---

### Post by d.j.schroeder on 2007-03-11
One small issue with all this.  Windows just seems to pick at random which interface to use for explorer.  So even if explorer is already open when you enable the other interface it may (or may not) just start using the newly enabled one.

---

### Post by Mr. C. on 2007-03-11
I think you are confused about networks.

You say you have two networks:

192.168.100.x
192.168.0.x

and the machines are::

Ubuntu: 192.168.100.x

WinXP: 192.168.0.X
         : 192.168.100.X

To use have TightVNC connect to the 192.168.0.X network, just tell it to connect to the address of the Ubuntu PC.  This works fine.  Windows does not pick random interfaces.

Show me what your netmasks are for the two networks, and show me where you router to the internet is configured.  Please use the actual addresses for each machine.

MrC

---

### Post by d.j.schroeder on 2007-03-13
I think you misunderstood my post.  TightVNC is working fine to connect to the Ubuntu machine.  But, if I have both network interfaces enabled on the widows PC explorer doesn't consistently use one or the other.  It seems to be choosing which interface to use at random.  TightVNC does not have this problem because I am telling it which subnet to use.

It is a bit of a problem for me (not at all major) that i can't get explorer to consistently use a particular interface.

---

### Post by Mr. C. on 2007-03-13
I probably did misunderstand.  So lets see if we can clarify it.

You have Ubuntu on the 100 network (192.168.100.0/24).  You have WinXP on the 0 network (192.168.0.0/24).  So far, you have two different networks.  How do these two networks communicate with each other?  You have not stated this, so I will assume they do not.  Therefore, with the one NIC connected on XP, you cannot reach your Ubuntu station.  Correct ?

Now, you also have another NIC in the XP station.  You connect it to the 100 network, and assign it an an address in that 100 network.  Now, you can use VNC to connect to and control Ubuntu from the Windows XP machine.  Windows XP will not send packets out the NIC on the 0 network, because their is no route to get there.  It should only send packets out the 100 NIC for all IP addresses on that 100 network.

Given this, I'm not seeing the problem, so there must be something that your not telling me about the setup.  Windows will not send out packets to randomly chosen NICs; it will send the packets to the interface that is listed in the route table.  Do a "route print" from a Windows command shell.

MrC

---

### Post by d.j.schroeder on 2007-03-14
> You have Ubuntu on the 100 network (192.168.100.0/24). You have WinXP on the 0 network (192.168.0.0/24). So far, you have two different networks. How do these two networks communicate with each other? You have not stated this, so I will assume they do not. Therefore, with the one NIC connected on XP, you cannot reach your Ubuntu station. Correct ?

I think that's correct.  On the XP machine one NIC, the one with the 0 network, is normally the only one I want enabled.  It does not connect to the 100 network.  When I want that machine to connect to the network containing the Ubuntu machine I enable a second on the XP machine which does connect to that network and uses a 100 address.  This is fine.

> Windows XP will not send packets out the NIC on the 0 network, because their is no route to get there. It should only send packets out the 100 NIC for all IP addresses on that 100 network.

This part seems not to be correct.  When I am connected to the 100 network (Ubuntu machine) I am also connected to the 0 network (what the XP machine normally uses).  So both networks are accessible by the XP machine.  In this case when I use a web browser on the XP machine (Firefox or Explorer) it sometimes goes through the gateway on the 0 network and sometimes goes through the gateway on the 100 network.

> Windows will not send out packets to randomly chosen NICs; it will send the packets to the interface that is listed in the route table. Do a "route print" from a Windows command shell.

It may not be random but it sure seems that way to me.  I did a "route print" unfortunately I can't seem to import it into this thread.  At the moment it does list the default gateway as 192.168.0.1, which it should.  But, sometimes it just switches to the other one.  I don't know why.

---

### Post by Mr. C. on 2007-03-14
> **d.j.schroeder said:**
> This part seems not to be correct.  When I am connected to the 100 network (Ubuntu machine) I am also connected to the 0 network (what the XP machine normally uses).  So both networks are accessible by the XP machine.  In this case when I use a web browser on the XP machine (Firefox or Explorer) it sometimes goes through the gateway on the 0 network and sometimes goes through the gateway on the 100 network.

What is connected on the other end of the WinXP 0 network ?  Is it your internet connection via some router ?  Is the Ubuntu machine hooked up to that too?  Windows will not send a packet destined for the 100 net down the 0 network line, unless you have a routing loop, or a subnet mask problem, which is what I suspect.  It knows how to send directly to the 100 network... i just places the packet on the 100 network wire and that's the shortest path.

You'll have to show your route table for this to make any sense.  Open a command window, right click the title bar, and select Properties.  On the Options tab, select Quick edit mode and click OK.  Say yes or no to the next dialog box.  Once the dialog is gone, do a "route print" command.  Then, with the mouse, select all the text on the screen, and hit the Enter key.  Then paste here.

Also show your ipconfig /all information for windows and ifconfig -a for ubuntu while both nic 0 and 1 are connected.

MrC

---

### Post by d.j.schroeder on 2007-03-14
Well first let me apologize for what I hope won't be another complication.  What we have been referring to as the 0 network in this thread is actually 10.  Long story and doesn't matter why, just 10 instead of 0.  I just can't seem to stop messing around with all this stuff.

Below are the two outputs that were requested.  But, the Ubuntu machine has only one network interface that is ever used (eth1 is used,  eth0 doesn't even have a wire plugged into it).  The Ubuntu machine is never connected to the 10 network.  And in answer to your question about what is at the end of the 10 network, yes there is a router connected to the internet.  There is a router connected to the 100 network which is connected to the internet also.  But they are NOT connected together, two totally separate internet connections, different providers.  One is a Comcast cable connection the other is a DSL connection from AT&T or whatever their name is this week.

> ===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x20002 ...00 15 f2 25 0c bf ...... NVIDIA nForce Networking Controller - Pa
 Scheduler Miniport
0xb0004 ...00 0e 0c b6 7a cc ...... Intel(R) PRO/1000 GT Desktop Adapter #2
cket Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     192.168.10.1  192.168.10.100       10
          0.0.0.0          0.0.0.0    192.168.100.1  192.168.100.197      20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
     192.168.10.0    255.255.255.0   192.168.10.100  192.168.10.100       10
   192.168.10.100  255.255.255.255        127.0.0.1       127.0.0.1       10
   192.168.10.255  255.255.255.255   192.168.10.100  192.168.10.100       10
    192.168.100.0    255.255.255.0  192.168.100.197  192.168.100.197      20
  192.168.100.197  255.255.255.255        127.0.0.1       127.0.0.1       20
  192.168.100.255  255.255.255.255  192.168.100.197  192.168.100.197      20
        224.0.0.0        240.0.0.0   192.168.10.100  192.168.10.100       10
        224.0.0.0        240.0.0.0  192.168.100.197  192.168.100.197      20
  255.255.255.255  255.255.255.255   192.168.10.100  192.168.10.100       1
  255.255.255.255  255.255.255.255  192.168.100.197  192.168.100.197      1
Default Gateway:      192.168.10.1
===========================================================================
Persistent Routes:
  None


For the Ubuntu machine:

> eth0      Link encap:Ethernet  HWaddr 00:09:6B:F4:67:1C
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2400 Memory:c4000000-c4020000

eth1      Link encap:Ethernet  HWaddr 00:40:05:06:9B:75
          inet addr:192.168.100.201  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe06:9b75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2732142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3629527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:443804255 (423.2 MiB)  TX bytes:2151469266 (2.0 GiB)
          Interrupt:11 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

---

### Post by Mr. C. on 2007-03-14
I've taken a quick look at your routing table, and ordered for readability.  You've confirmed my suspicions with your last post.

```
Active  Routes:
Network Dest         Netmask              Gateway              Interface          Metric

127.0.0.0            255.0.0.0            127.0.0.1            127.0.0.1          1 
192.168.10.100       255.255.255.255      127.0.0.1            127.0.0.1          10
192.168.100.197      255.255.255.255      127.0.0.1            127.0.0.1          20

192.168.10.0         255.255.255.0        192.168.10.100       192.168.10.100     10
192.168.10.255       255.255.255.255      192.168.10.100       192.168.10.100     10

192.168.100.0        255.255.255.0        192.168.100.197      192.168.100.197    20
192.168.100.255      255.255.255.255      192.168.100.197      192.168.100.197    20

255.255.255.255      255.255.255.255      192.168.10.100       192.168.10.100     1 
255.255.255.255      255.255.255.255      192.168.100.197      192.168.100.197    1 

0.0.0.0              0.0.0.0              192.168.10.1         192.168.10.100     10
0.0.0.0              0.0.0.0              192.168.100.1        192.168.100.197    20

224.0.0.0            240.0.0.0            192.168.10.100       192.168.10.100     10
224.0.0.0            240.0.0.0            192.168.100.197      192.168.100.197    20
Default Gateway:     192.168.10.1
```

You have two distinct networks joined by NATing devices.  This creates a problem.

See:  [http://support.microsoft.com/kb/299540](http://support.microsoft.com/kb/299540)

> NOTE: Typically, Microsoft does not recommend that you add default gateways across disjoint networks. For example, edge servers, such as, Network Address Translation (NAT) and proxy servers, are typically configured to connect two or more disjoint networks: The public Internet and one or more private intranets. In this situation, you should not assign the default gateways on the private interfaces, as doing so may result in improper routing on your network.

You have two default gateways, with two NATing devices.  Remove one of the default gateways.

MrC

---

### Post by d.j.schroeder on 2007-03-16
Ok, I think I've removed the default gateway from the second interface.  Actually, everything was automatic before, but now I've entered everything manually for that one and have left the default gateway blank.  Hopefully, this fixes it.

Thank you for your help.

---

### Post by Mr. C. on 2007-03-16
You're welcome.  Let us know how things workout.

MrC

---

### Post by d.j.schroeder on 2007-03-22
I've been using this a tone over the last week or so.  No problems at all since making the changes you suggested.

Thanks again.

---

### Post by Mr. C. on 2007-03-22
Fantastic!

Thanks for the update,
MrC

---

