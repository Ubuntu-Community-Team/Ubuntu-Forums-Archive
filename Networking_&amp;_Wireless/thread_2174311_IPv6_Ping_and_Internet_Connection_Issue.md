---
title: "IPv6 Ping and Internet Connection Issue"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by bijan2 on 2013-09-13
[COLOR=#000000][FONT=Verdana]Hi, I've managed to get IPv6 working om my D-link router (DIR-645),  please see the attached photos. I can ping IPv6 addresses _ONLY_ within the router configuration page, but not from my laptop terminal.  I can not visit any of the IPv6 web sites, only IPv4 sites are available.
Not sure what the problem is, the router has the latest Firmware (1.04) and [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Ubuntu firewall is inactive but still can not connect. 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]I appreciate any help you can provide...
TIA[/FONT][/COLOR]

---

### Post by sanderj on 2013-09-14
OK, your d-link had IPv6 connectivity. But how do you distribute / advertise IPv6 connectivity to your LAN. What does "ifconfig" of your computer say?

---

### Post by bijan2 on 2013-09-14
Thanks for your reply, I have attached a copy of "ifconfig".

---

### Post by sanderj on 2013-09-14
Looks good: your system has public IPv6 addresses! Checking: your system received those addresses automatically from your d-link, right? You have NOT manually configured on your Linux system?

Next tests:

what does [http://test-ipv6.com/](http://test-ipv6.com/) say?

what is the output of:

```

mtr -nrc5 ipv6.google.com
ip -6 route show

```

Post the output here.

---

### Post by bijan2 on 2013-09-14
No I actually got all those numbers (duplicated manually) from Comcast Modem configuration page that is connected directly to my 2nd laptop. The Comcast Modem connected to the Dlink and is doing a good job as far as assigning IPv4 addresses but not sure how they communicate with each other as far as IPv6 goes (Prefix,etc...).

bijan@U56E ~ $ mtr -nrc5 ipv6.google.com
HOST: U56E                        Loss%   Snt   Last   Avg  Best  Wrst StDev
bijan@U56E ~ $ ip -6 route show
2601:8:8a80:38::/64 dev eth0  proto kernel  metric 256  expires 86266sec
fe80::/64 dev eth0  proto kernel  metric 256 
default via fe80::2a10:7bff:fef2:d95c dev eth0  proto static  metric 1 
default via fe80::2a10:7bff:fef2:d95c dev eth0  proto ra  metric 1024  expires 3466sec
bijan@U56E ~ $

---

### Post by bijan2 on 2013-09-14
[COLOR=#000000]I am sorry, [/COLOR][http://test-ipv6.com/](http://test-ipv6.com/)[COLOR=#000000] says no IPv6 address detected....[/COLOR]

---

### Post by sanderj on 2013-09-14
You copied the IPv6 addresses manually to your computer? That's not how you should do it. Your computer should get the IPv6 address automatically via RADVD or DHCPv6. So remove the manually added IPv6 addresses from your Linux system and do a fresh reboot. Then go back to your D-Link and search for the option 'RADVD' or " DHCPv6" and set the checkbox to "yes"

You use 2601:8::, so ComCast. Which setup instruction from ComCast do you use? I'm surprised you're using static IPv6; I would expect something more automatic (I use 6RD on my D-link, and that works great ...)

---

### Post by bijan2 on 2013-09-14
Thank you, I was told by Dlink Support to use Static IPv6 instead of the other options. I do not have RADVD but have SLAAC/DHCPv6. Which I can try but for some reason that option does not record/register the DNS server primary and secondary numbers on the Status page. Not sure why but I'll give that a try and report...

---

### Post by sanderj on 2013-09-14
So: with DHCPv6 you do get an IPv6 address on your Linux? That would be nice. Run the commands I gave you: test-ipv6, mtr, ip

Furthermore: a DNS with only a IPv4 address will also resolve IPv6 addresses (see example below), so no need there.


```
sander@flappie:~$ host www.facebook.com 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

www.facebook.com is an alias for star.c10r.facebook.com.
star.c10r.facebook.com has address 31.13.64.113
star.c10r.facebook.com has IPv6 address 2a03:2880:10:8f07:face:b00c:0:1
star.c10r.facebook.com mail is handled by 10 msgin.t.facebook.com.
sander@flappie:~$ 
```

---

### Post by bijan2 on 2013-09-14
Thank you, That is good to know that that IPv4 resolve IPv6 addresses. Unfortunately I am not getting an IPv6 address. Please see the attached...

---

### Post by sanderj on 2013-09-14
What is the instruction from Comcast?

---

### Post by bijan2 on 2013-09-14
There is really no instruction at all. As I mentioned connecting to Comcast router directly you can access the configuration page by typing 10.0.0.1 and get all the numbers...That is why I use Static IPv6 setup and copied everything to DLink, Indeed very tedious task...
Perhaps I have an issue with the Dlink "bad" firmware which I am trying to convince their tech support.
I will follow again tomorrow with the other options but my chances are slim. It is very late here and I'll report tomorrow. I appreciate all your help and will continue later.

---

### Post by bijan2 on 2013-09-14
Hi, Changed a few things and here is the result:

bijan@U56E ~ $ ip -6 route show
2601:8:8a80:38::/64 dev eth0  proto kernel  metric 256  expires 86370sec
fe80::/64 dev eth0  proto kernel  metric 256 
default via fe80::2a10:7bff:fef2:d95c dev eth0  proto ra  metric 1024  expires 3570sec
bijan@U56E ~ $


bijan@U56E ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:60:00:33:c1:a8  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2601:8:8a80:38:ca60:ff:fe33:c1a8/64 Scope:Global
          inet6 addr: fe80::ca60:ff:fe33:c1a8/64 Scope:Link
          inet6 addr: 2601:8:8a80:38:f125:696b:f0a4:1f99/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5881 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:7395479 (7.3 MB)  TX bytes:722230 (722.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53106 (53.1 KB)  TX bytes:53106 (53.1 KB)


bijan@U56E ~ $


and here is the IPv6 Status within the Dlink router:
[COLOR=#000000][FONT=Tahoma][h=2]IPV6 CONNECTION INFORMATION[/h][RIGHT]**IPv6 Connection Type**[/RIGHT][CENTER]**:**[/CENTER]Autoconfiguration (SLAAC/DHCPV6)
[RIGHT]**Network Status**[/RIGHT][CENTER]**:**[/CENTER]Connected
[RIGHT]**Connection Up Time**[/RIGHT][CENTER]**:**[/CENTER]0 Day 0 Hour 0 Min 0 Sec
[RIGHT]****[/RIGHT][CENTER]****[/CENTER]   
[RIGHT]**WAN IPv6 Address**[/RIGHT][CENTER]**:**[/CENTER]2601:8:8a80:38:2a10:7bff:fef2:d95d /64

[RIGHT]**IPv6 Default Gateway**[/RIGHT][CENTER]**:**[/CENTER]fe80::21d:d6ff:feb1:3af1
[RIGHT]**Primary IPv6 DNS Server**[/RIGHT][CENTER]**:**[/CENTER]None
[RIGHT]**Secondary IPv6 DNS Server**[/RIGHT][CENTER]**:**[/CENTER]None
[RIGHT]**LAN IPv6 Link-Local Address**[/RIGHT][CENTER]**:**[/CENTER]fe80::2a10:7bff:fef2:d95c /64
[RIGHT]**DHCP-PD**[/RIGHT][CENTER]**:**[/CENTER]Enabled
[RIGHT]**IPv6 Network assigned by DHCP-PD**[/RIGHT][CENTER]**:**[/CENTER]None
[RIGHT]**LAN IPv6 Address**[/RIGHT][CENTER]**:**[/CENTER]2601:8:8a80:38:185d:673c:6f66:37b9 /64

[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][/FONT][/COLOR]

---

### Post by bijan2 on 2013-09-14
Here are more data to review, I have to use Static IPv6 in order to get the DNSs to show up on Status page:
Still the same issue exist.

---

### Post by sanderj on 2013-09-14
Once again: 
did you manually configure the IPv6 addresses on your linux system? If so: don't do that. That's not the way to do it, and it makes analyses more complex
do not bother about DNS-over-ipv6


Without instructions from Comcast I think it is trial-n-error to get it working. IPv6 has too much parameters to get it working that way. You might try [http://ipvsix.me/?p=220](http://ipvsix.me/?p=220) to see if that works

I don't think your D-link has a bug; IPv6 works on my D-link (with 6RD).

---

### Post by bijan2 on 2013-09-15
Thanks for your input, the answer to your question is NO, nothing was changed with my Linux OS, I only change the numbers within DIR-645 configuration page. Your forwarded link was helpful and I have set my IPv6 just like it was recommended there (DIR-825) but still no IPv6 connection here. I am working on it and hope I can get it to work. I'll update as I go forward with this... Thank you,

---

### Post by bijan2 on 2013-09-20
A quick update, This is somehow strange. The D-Link router finally gets an IPv6 address via 6to4 tunnel (status page looks good) and I can ping6 some sites from Ubuntu terminal but I get the message (....icmp_seq=5 Destination unreachable: No route).
 ifconfig also looks good and shows 2 Scope:Global addresses + 1 Link address.
The  [http://test-ipv6.com/](http://test-ipv6.com/) tells me no IPv6 address detected and I can not visit any of the IPv6 web sites but I can see an IPv6 address when I issue nm-tool command. Not sure what the problem is, maybe a firewall is blocking the sites.
Please see the next post for some commands outputs. I appreciate any help you can provide. ...
TIA

---

### Post by bijan2 on 2013-09-20
[COLOR=#000000][FONT=verdana]Please check what I have posted here. Perhaps a firewall on my Linux system or on my LAN blocking the web-traffic. BTW, the [/FONT][/COLOR][COLOR=#000000][FONT=verdana]web browser is not using a proxy.[/FONT][/COLOR]

bijan@U56E ~ $ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=0.380 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=0.349 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=0.369 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=0.365 ms

bijan@U56E ~ $ mtr -c4 -r -n 8.8.8.8
HOST: U56E                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 10.0.0.1                   0.0%     4    1.0   1.1   0.9   1.4   0.2
  2.|-- 73.96.166.1                0.0%     4    9.6  12.8   9.6  20.8   5.4
  3.|-- 68.86.113.185              0.0%     4    9.7  10.4   8.5  13.8   2.3
  4.|-- 69.139.164.185             0.0%     4   12.5  18.3  10.2  34.5  11.0
  5.|-- 68.86.93.165               0.0%     4   15.6  13.9  12.4  15.6   1.7
    |  `|-- 68.86.93.5
    |   |-- 68.86.92.33
    |   |-- 68.86.93.173
  6.|-- 68.86.84.106               0.0%     4   13.4  11.8  10.5  13.4   1.2
  7.|-- 75.149.231.90              0.0%     4   12.3  11.9  11.0  13.1   1.0
  8.|-- 209.85.249.34              0.0%     4   10.7  15.5  10.6  22.6   5.9
  9.|-- 66.249.94.197              0.0%     4   21.5  15.3  11.7  21.5   4.3
    |  `|-- 66.249.94.201
 10.|-- 216.239.46.200             0.0%     4   20.1  21.4  19.5  25.3   2.6
 11.|-- 216.239.48.167             0.0%     4   21.0  19.8  18.7  21.0   1.0
    |  `|-- 64.233.174.129
    |   |-- 64.233.174.131
 12.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
 13.|-- 8.8.8.8                    0.0%     4   40.0  28.8  20.0  40.0   8.3



bijan@U56E ~ $ wget [www.google.com]("http://www.google.com")
--2013-09-20 17:55:46--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com]("http://www.google.com") ([www.google.com]("http://www.google.com"))... 74.125.28.104, 74.125.28.99, 74.125.28.103, ...
Connecting to [www.google.com]("http://www.google.com") ([www.google.com)|74.125.28.104|:80]("http://www.google.com)|74.125.28.104|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html&#8217;


    [ <=>                                   ] 10,615      --.-K/s   in 0.001s  


2013-09-20 17:55:46 (9.10 MB/s) - &#8216;index.html&#8217; saved [10615]


bijan@U56E ~ $ ping6 ipv6.google.comPING ipv6.google.com(pc-in-x68.1e100.net) 56 data bytes
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=1 Destination unreachable: No route
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=2 Destination unreachable: No route
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=3 Destination unreachable: No route
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=4 Destination unreachable: No route
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=5 Destination unreachable: No route
From 2002:a00:3:2601:2a10:7bff:fef2:d95c icmp_seq=6 Destination unreachable: No route
^C
--- ipv6.google.com ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5007ms


bijan@U56E ~ $

---

### Post by sanderj on 2013-09-21
> **bijan2 said:**
> A quick update, This is somehow strange. The D-Link router finally gets an IPv6 address via 6to4 tunnel (status page looks good) and I can ping6 some sites from Ubuntu terminal but I get the message (....icmp_seq=5 Destination unreachable: No route).

That is not a succesfull ping6.

Anyway, if you're OK with a tunnel to get IPv6, do this: 

```
sudo apt-get install miredo
```

Then visit [http://test-ipv6.com/](http://test-ipv6.com/)

---

### Post by bijan2 on 2013-09-21
Thank you again, I'll consider that but I actually like to use Native IPv6 of Comcast if I can. I did get a call from D-Link Network Engineer yesterday, they had me to switch back to SLAAC/DHPCv6 option again. But unfortunately that does not pickup any IPv6 address from Comcast Arris modem. They are kind of puzzled by why when I am connected to Arris all works fine but DIR-645 can't handle it.
I also read on Comcast forum that other people having similar issues and Comcast engineer thinks it has something to do with SLAAC part of DHCPv6. 
I am using Automatic option of Ubuntu IPv6 but I guess I can change it to "Automatic, DHCP Only" option if that makes a difference...  I'll update again.

---

### Post by bijan2 on 2013-09-22
[COLOR=#3B3B3B][FONT=Helvetica Neue]The WAN IPv6 address was set incorrectly (2601:), that is Comcast PD space not their WAN space.. Problem Solved

Thanks for all your support...[/FONT][/COLOR]

---

### Post by sanderj on 2013-09-23
> **bijan2 said:**
> [COLOR=#3B3B3B][FONT=Helvetica Neue]The WAN IPv6 address was set incorrectly (2601:), that is Comcast PD space not their WAN space.. Problem Solved

Thanks for all your support...[/FONT][/COLOR]

Great. Can you post an overview of the settings so that it can help others? So: the IPv6 settings in your router. You can black-out your specific details, so somewhere in the middle of your IPv6 addresses.

---

