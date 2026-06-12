---
title: "Internal Network Fine, Internet or WAN access.. FUBAR"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by mbmonk on 2005-08-02
I can move around in my internal network (at work) but internet access (WAN) is non-existant.

Here are somelogs:
 \\:D/ 
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:11:43:76:ED:7F  
          inet addr:192.168.0.125  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe76:ed7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29033 (28.3 KiB)  TX bytes:2710 (2.6 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18400 (17.9 KiB)  TX bytes:18400 (17.9 KiB)


 [-X 
Me trying to ping outside the LAN:

PING [www.nfl.com](www.nfl.com) (216.19.170.247) 56(84) bytes of data.

--- [www.nfl.com](www.nfl.com) ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8998ms


 \\:D/ 
Pinging inside the network LAN:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=1.27 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=1.21 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=128 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=128 time=1.41 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=128 time=1.31 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=128 time=2.48 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=128 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=128 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=128 time=1.37 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=128 time=1.27 ms

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9008ms
rtt min/avg/max/mdev = 1.218/1.455/2.483/0.350 ms
e log files:




Ok so I have no idea how to troubleshoot this. The hardware is working I would assume.

Please give me any commands I can use to help you help me :).

BTW, the servers that control WAN access are windows, dont know if that helps or not.

Thanks,
Mike

---

### Post by KLineD on 2005-08-02
Check /etc/resolv.conf to see if you have your DNS set up correctly

---

### Post by mbmonk on 2005-08-02
Here is the contents of my resolve.conf:

search buel
nameserver 192.168.0.254










I can get on the network with my windows machine and the DNS server is the address specified above.

Also I was able to ping the address above from ubuntu so the dns server is alive and reachable.


Does that resolve.conf look right?


Thanks for taking the time to give me ideas. What next should I do?

---

### Post by cwaldbieser on 2005-08-02
If you can't ping a raw IP address outside the network, DNS is not your problem.  What does your routing table look like?

```
$ route
```

Maybe you just don't have your default gateway set correctly?

Another possiblitly could be that you have a firewall (like firestarter) running on Ubuntu?  There isn't one by default, but you could have installed one?

---

### Post by KLineD on 2005-08-02
is that search address correct? (buel)

also try posting a little info about your network connection (cable, DSL, router, how are you connected?) so we can try to pinpoint the problem with better results.

---

### Post by mbmonk on 2005-08-02
The network I am on is a small business network. It has a DHCP server and DNS server.  My laptop (The machine in question) gets an IP and all relevant info from the DHCP server. That part seems to be successful, DCHP that is. That is what makes this hard to comprhened.

So I am on the inside of a small business network.

Here are my route tables:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         buel2.buel.com  0.0.0.0         UG    0      0        0 eth0
default         192.168.0.2     0.0.0.0         UG    0      0        0 eth0



Here is my IPCONFIG from my laptop running XP (Dual Boot)  this os gets WAN access:
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.0.125
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.0.2
                                    192.168.0.1
DHCP Server . . . . . . . . . . . : 192.168.0.254
DNS Servers . . . . . . . . . . . : 192.168.0.254
Primary WINS Server . . . . . . . : 192.168.0.254
Lease Obtained. . . . . . . . . . : Tuesday, August

Lease Expires . . . . . . . . . . : Thursday, Septe




So I hope that helps.

For the "search buel" part of my resolve.conf it should be buel.com but I have changed that back and forth a million times :).  Also to my knowledge I have not installed a firewall. I dont have access to WAN so I ASSUME that I couldnt get apps from apt-get or synaptic. I did mess around with them but I didnt not install them to my knowledge.

Thanks guys for taking the time to look at this.

---

### Post by cwaldbieser on 2005-08-03
The fact that you have two default routes seems wrong to me.  I would reccomend getting rid of the "buel2.buel.com 0.0.0.0" route.

```
$ sudo route del -net 0.0.0.0
```
of course, this could delete your second default route as well (not really sure how it's possible to have two identical routes in the first place).  You can just add the real default back:

```
$sudo route add -net default gw 192.168.0.2
```

---

### Post by digitalmouse on 2005-08-03
not meaning to hi-jack this thread- but it appears i have a similar problem:

```
root@doormouse:/home/digitalmouse # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:FC:20:12:17
          inet addr:10.0.0.200  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe20:1217/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2705844 (2.5 MiB)  TX bytes:3623034 (3.4 MiB)
          Interrupt:10 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:984 (984.0 b)  TX bytes:984 (984.0 b)

root@doormouse:/home/digitalmouse # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        255.255.255.0   UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0

root@doormouse:/home/digitalmouse # cat /etc/resolv.conf
search wonderland
nameserver 10.0.0.1

root@doormouse:/home/digitalmouse # ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=127 time=0.576 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=127 time=0.552 ms

root@doormouse:/home/digitalmouse # ping 10.0.0.11
PING 10.0.0.11 (10.0.0.11) 56(84) bytes of data.
64 bytes from 10.0.0.11: icmp_seq=1 ttl=64 time=1.40 ms
64 bytes from 10.0.0.11: icmp_seq=2 ttl=64 time=0.229 ms
64 bytes from 10.0.0.11: icmp_seq=3 ttl=64 time=0.219 ms

root@doormouse:/home/digitalmouse # ping www.google.com
connect: Network is unreachable
root@doormouse:/home/digitalmouse # ping 64.233.161.104
connect: Network is unreachable



``` 

at first glance it looks ok, but i get the feeling i am missing something. 

 ](*,)

---

### Post by mbmonk on 2005-08-03
```
$ sudo route del -net 0.0.0.0
```


You figured it out. That was it. Internet is working now :). 

Thank You cwaldbieser and KLineD. I appreciate you looking at this and solving it. :P

Thank you.

---

### Post by cwaldbieser on 2005-08-03
Is your computer connected directly to the Internet?  From the route settings, I'd guess that you are plugged into a router with address 10.0.0.1, but since you are having problems I thought I had better ask.

---

### Post by digitalmouse on 2005-08-04
whoops!  thought i posted a reply about my problem.

i looked over a MEPIS-Linux server i set up over a year ago, and compared the route tables:

```
// MEPIS server:
digitalmouse@1[~]$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0

// ubuntu server:
digitalmouse@doormouse:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
default         10.0.0.1        255.255.255.0   UG    0      0        0 eth0

``` 

when i removed the Genmask/netmask from the gateway entry (deleted the entry, then re-entered it without the mask), the machine could ping the outside world and i could access it remotely.

thanks for letting me babble out loud- guess i should do this more often.  i fix more problems that way!

 :)

---

