---
title: "Networking Problems (traceroute and amazonmp3 can't get through)"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by JPurdy on 2008-05-19
I'm having some weird networking problems and I can't figure out how to diagnose what's going on. These problems seemed to show up once I upgraded to Heron, though it could be related to a new router, too. Regardless, can someone point me to some tools that might help me identify where the problem lies, exactly?

First, the 'amazonmp3' application no longer can connect to download music I bought. I went through the remove --purge and reinstalled it, just in case that was it, but it wasn't. I fired up Etherape as root to snoop the traffic and I don't see anything, so perhaps it's an application problem?

My other problem is that 'traceroute' doesn't seem to do anything. I am getting a DHCP IP address and I can ping the router and I can ping internal and external locations[1]. But traceroute just stalls[2].

So I'm thinking it's a weird firewall issue or maybe some sort of traffic prohibition? But I don't have anything in iptables[3] (if that's still being used) and ufw reports that the firewall is disabled[4].

Thanks!

[1]
```
$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.964 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.651 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.651/0.807/0.964/0.159 ms
$ ping 192.168.2.157
PING 192.168.2.157 (192.168.2.157) 56(84) bytes of data.
64 bytes from 192.168.2.157: icmp_seq=1 ttl=128 time=3.80 ms
64 bytes from 192.168.2.157: icmp_seq=2 ttl=128 time=0.352 ms

--- 192.168.2.157 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1007ms
rtt min/avg/max/mdev = 0.352/2.078/3.804/1.726 ms
jason@jason:~$ ping www.google.com
PING www.l.google.com (209.85.165.99) 56(84) bytes of data.
64 bytes from eo-in-f99.google.com (209.85.165.99): icmp_seq=1 ttl=243 time=33.7 ms
64 bytes from eo-in-f99.google.com (209.85.165.99): icmp_seq=2 ttl=243 time=32.0 ms

--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 32.015/32.895/33.776/0.898 ms

```
[2]
```
$ traceroute www.google.com
traceroute to www.google.com (209.85.165.103), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * *
```

[3]
```

$ sudo ufw status
Firewall not loaded
$ sudo ufw disable
Firewall stopped and disabled on system startup

```

[4]
```

$ sudo iptables -L
[sudo] password for jason: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by JPurdy on 2008-05-19
I have VirtualBox w/ Windows XP installed on my Ubuntu box and so I fired that up to test the Amazon Downloader and it works perfectly. So now I'm back to thinking it's something wrong w/ my Ubuntu setup.

---

### Post by BFris on 2008-05-29
same problem here. amazonmp3 dead after heron upgrade. In my case I'm running AMD64 Kubuntu. But I had everything working fine in gutsy after the getlibs trick.

???

---

### Post by BFris on 2008-05-29
Well, after more digging the solution seems to be to disable ipv6 networking. To do this, you need to add these lines to your /etc/modules.d/blacklist file:
```
blacklist ipv6
```
Then you have to reboot. There must be a way to manually unload the necessary module, but I couldn't figure out how to do it.

Here are some of the links I followed to figure it all out:

[http://ubuntuforums.org/showthread.php?t=763576]("http://ubuntuforums.org/showthread.php?t=763576")

[http://ubuntuforums.org/showthread.php?t=772396&highlight=flock]("http://ubuntuforums.org/showthread.php?t=772396&highlight=flock")

[http://ubuntuforums.org/showthread.php?t=674401]("http://ubuntuforums.org/showthread.php?t=674401")

---

