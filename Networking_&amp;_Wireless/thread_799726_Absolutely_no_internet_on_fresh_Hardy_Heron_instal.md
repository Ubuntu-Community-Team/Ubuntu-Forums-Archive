---
title: "Absolutely no internet on fresh Hardy Heron install - Atheros AR5007EG"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Eax.exe on 2008-05-19
Hello.

I just installed Hardy Heron on my Acer TravelMate 4310.
It only managed to install it with "acpi=off".

I have an Atheros AR5007EG Wireless card.

My problem is that there is absolutely NO internet connection.
What so ever.
It doesn't even recognize my Wireless Interface.
The most troubling is that it sees that there is Wired connection but it can't connect.

Any help would be greatly appreciated :)

Thanks in advance :D

---

### Post by raiwo on 2008-05-19
there is several threads about AR5007 card, how about using search next time?

[http://ubuntuforums.org/showthread.php?t=792158&highlight=Atheros+AR5007EG](http://ubuntuforums.org/showthread.php?t=792158&highlight=Atheros+AR5007EG)

---

### Post by Eax.exe on 2008-05-19
No offense ment. But how about you read my post?
I DON'T! Have wired net, which the link you provided and all the search results I found assumed I had.

---

### Post by Monicker on 2008-05-19
What are the results of the following commands
```

sudo ifconfig
netstat -rn
```


Your wired interface is normally eth0, so also run this
```

sudo ethtool eth0
```

---

### Post by Eax.exe on 2008-05-19
> **Monicker said:**
> What are the results of the following commands
```

sudo ifconfig
netstat -rn
```


Your wired interface is normally eth0, so also run this
```

sudo ethtool eth0
```

The ´sudo ifconfig´ outputs the following interfaces ´eth0 and lo´
And the info about them.

´netstat -rn´:
Destination   Gateway       Genmask Flags  MSS Window irtt Iface
192.168.10.0  0.0.0.0       255.255.255.0  U          0     eth0
169.254.0.0   0.0.0.0       255.255.0.0    U          0     eth0
0.0.0.0       192.168.10.1  0.0.0.0        UG         0     eth0

the ethtool eth0 outputs this:
´Settings for eth0
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
                      10baserT/Half 10baserT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
                       10baseT/Half 10baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 32
Transceiver: internal
Auto-negotiation: On
Supports Wake-on: pumbg
Wake-on: d
Current message level: 0x0000007 (7)
Link detected: Yes´

That´s it :)
Any ideas?

---

### Post by Monicker on 2008-05-19
Hrmm. Your wired interface has an ip address assigned and ethtool shows a good connection.

Were you trying to reach a web site and were not able to?

Copy/paste the following commands.

```
ping -c 4 4.2.2.2
ping -c 4 ping.symantec.com
```

Your results should be similar to the following:

```
arkaic@incognito:~$ ping -c 4 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=244 time=19.5 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=244 time=21.3 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=244 time=19.7 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=244 time=20.0 ms

--- 4.2.2.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 19.531/20.166/21.398/0.738 ms


arkaic@incognito:~$ ping -c 4 ping.symantec.com
PING ping.symantec.com (206.204.18.22) 56(84) bytes of data.
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=1 ttl=239 time=29.4 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=2 ttl=239 time=28.8 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=3 ttl=239 time=31.5 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=4 ttl=239 time=31.8 ms

--- ping.symantec.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 28.878/30.429/31.806/1.281 ms

```

Also give the output of
```

cat /etc/resolv.conf
```

---

### Post by Eax.exe on 2008-05-19
> **Monicker said:**
> Hrmm. Your wired interface has an ip address assigned and ethtool shows a good connection.

Were you trying to reach a web site and were not able to?

Copy/paste the following commands.

```
ping -c 4 4.2.2.2
ping -c 4 ping.symantec.com
```

Your results should be similar to the following:

```
arkaic@incognito:~$ ping -c 4 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=244 time=19.5 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=244 time=21.3 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=244 time=19.7 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=244 time=20.0 ms

--- 4.2.2.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 19.531/20.166/21.398/0.738 ms


arkaic@incognito:~$ ping -c 4 ping.symantec.com
PING ping.symantec.com (206.204.18.22) 56(84) bytes of data.
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=1 ttl=239 time=29.4 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=2 ttl=239 time=28.8 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=3 ttl=239 time=31.5 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=4 ttl=239 time=31.8 ms

--- ping.symantec.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 28.878/30.429/31.806/1.281 ms

```

Also give the output of
```

cat /etc/resolv.conf
```

Yes I were trying to reach something as simple as google. Didn´t go trough :(

The first ping:
´
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
From 192.168.10.51 icmp_seq=2 Destination Host Unreachable
From 192.168.10.51 icmp_seq=3 Destination Host Unreachable
From 192.168.10.51 icmp_seq=4 Destination Host Unreachable

--- 4.2.2.2 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3000ms, pipe 3´

The second:
´ping: unknown host ping.symantec.com´

Oo

From the ´cat /etc/resolv.conf´:
´Begin info
modified_by: NetworkManager
Process: /usr/bin/NetworkManager
Process_id: 4345

END INFO

search keef.local

nameserver 192.168.10.2´

Weird :S

---

### Post by Monicker on 2008-05-19
Interesting.  Did you set a static ip in Network Manager, or are you using DHCP?  Normally with a home router the gateway address and the nameserver will be the same ip.  It seems like there is a mismatch somewhere.

Can you ping both 192.168.10.1 and 192.168.10.2 ?  Do either of those addresses seem familiar as belonging to your home router?

---

### Post by Eax.exe on 2008-05-19
> **Monicker said:**
> Interesting.  Did you set a static ip in Network Manager, or are you using DHCP?  Normally with a home router the gateway address and the nameserver will be the same ip.  It seems like there is a mismatch somewhere.

Can you ping both 192.168.10.1 and 192.168.10.2 ?  Do either of those addresses seem familiar as belonging to your home router?

I can't ping either :(
I do recognize 192.168.10.2 as the server functioning as a router here :)

---

### Post by Monicker on 2008-05-19
Your netstat shows that the machine thinks it should be using 192.168.10.1 as its default gateway.  Which is going to be a problem if nothing actually exists at that address.  :)  You should still be able to ping 192.168.10.2 however.  Verify your network settings.

System -> Administration -> Network

Unlock it and check the properties for the wired connection.  Do you have it set for a static ip, and if so what is the gateway?  It should be 192.168.10.2.

Verify your settings on the server also.  Make sure its not giving out bad dhcp information, if that is what you are using instead of a static ip.  It could be an issue with the server itself.

---

### Post by Eax.exe on 2008-05-21
I did all that. Still doesn´t work :(
Tried changing network to a different one. Doesn´t work either :S

Sorry for the late answer also, had to travel across the country :P

Any other ideas?

---

### Post by Eax.exe on 2008-05-31
Anyone?

---

