---
title: "Unable to access internet"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by ickyfeet on 2007-03-21
I have lost the ability to access the internet from my computer.  I am able to connect to my routers web interface through my computer and I'm able to connect to the internet via my wife's computer which is connected to said router.   Any suggestions?  I'm new to linux and still trying to figure out how to hunt problems down.  Any help would be appreciated.

---

### Post by Paul41 on 2007-03-22
I could be a IPv6 problem.  You could try to disable it to see if that fixes your problem.  Assuming you are using Firefox, type about:config in the address bar.  On the page that comes up filter for IPv6 and disable it.

---

### Post by MrCheese on 2007-03-22
make sure your router is set as your default gateway

---

### Post by dbott67 on 2007-03-22
We need to determine whether you have connectivity past the router.  According to your post, you are able to login to the router.  Can you please post the output of the following commands:

1. **ping 64.233.161.104**

By pinging using IP address only, we will be able to test for external connectivity.  If you get "replies" it means that your computer can "see" the computer at 64.233.161.104 (which is the IP address of one of google's servers).  No replies means that your computer is unable to see past the router:

```

dbott@thedrake:~$ [COLOR=Blue]**ping 64.233.161.104**[/COLOR]
PING 64.233.161.104 (64.233.161.104) 56(84) bytes of data.
64 bytes from 64.233.161.104: icmp_seq=1 ttl=234 time=46.0 ms
64 bytes from 64.233.161.104: icmp_seq=2 ttl=234 time=47.9 ms
64 bytes from 64.233.161.104: icmp_seq=3 ttl=234 time=43.3 ms

--- 64.233.161.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 43.398/45.790/47.957/1.876 ms

```If you are unable to ping via IP address, it may be as MrCheese suggests a default route/gateway problem.  Can you please post the output of the following 2 commands:
```
dbott@thedrake:~$** [COLOR=Blue]ifconfig[/COLOR]**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          inet addr:[COLOR=Red]192.168.1.106[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0 [COLOR=Red]*<--my IP in red*[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1103281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1074733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:850828062 (811.4 MiB)  TX bytes:344571545 (328.6 MiB)
          Interrupt:185 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:397174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:222863942 (212.5 MiB)  TX bytes:222863942 (212.5 MiB)

``````
dbott@thedrake:~$ [COLOR=Blue]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         [COLOR=Red]192.168.1.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0 *[COLOR=Red]<-- my router IP in red[/COLOR]*

```

2. If pinging via IP works, the next step is to test using a fully-qualified domain name ([www.google.com):]("http://www.google.com%29:")
```
dbott@thedrake:~$ [COLOR=Blue]**ping www.google.com**[/COLOR]
PING www.l.google.com (64.233.161.104) 56(84) bytes of data.
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=1 ttl=234 time=45.5 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=2 ttl=234 time=47.3 ms
64 bytes from od-in-f104.google.com (64.233.161.104): icmp_seq=3 ttl=234 time=47.0 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 45.547/46.642/47.371/0.827 ms

```

At this point, if you do not get any replies then it leads towards a **DNS issue **(which is common for some brands of less-expensive routers) or possibly an **IPv6 issue** (as Paul41 suggests). 

_**Fixing DNS & IPv6 Issues**_

You may want to try 2 things:

1. Blacklist ipv6
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747 ]("http://www.ubuntuforums.org/showthread.php?t=323747")

There is plenty of debate about the validity of blacklisting IPv6.  I've never had a problem with it, yet there are many that do and blacklisting it seems to fix the problem.  Be sure to document what you try, as you may want to undo it later.

-Dave

---

### Post by ickyfeet on 2007-03-22
Thanks for the help guys . . .  I fixed the problem . . . I don't know what the problem was exactly.  I had DDNS setup on my linksys router to update my ip via dyndns.org and as soon as I disabled it everything started working properly???  Thanks for the help.

---

