---
title: "internet problems"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by BlackWingAngel on 2005-10-26
Hi
I've a router and my pc is connected to this by a cable, I don't have a dhcp server and I've assigned manually the IP address (using the option static ip address on the pc and adding a host on the router) but I can't connect to internet!! 
when i use the command: ifconfig eth0 this is the result:

eth0      Link encap:Ethernet  HWaddr 00:11:2F:5B:AB:95  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe5b:ab95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68391 (66.7 KiB)  TX bytes:17800 (17.3 KiB)
          Interrupt:17 
and when i use ping 192.168.1.1(the router IP) this is the risult: 

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.715 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.685 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.685 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.692 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.691 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.682 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.679 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.677 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.688 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.676 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.682 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.684 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=255 time=0.690 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=0.683 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=0.671 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=0.678 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=0.684 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=255 time=0.686 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=255 time=0.682 ms

infinite times!! But when I ping the pc from the router it works very well

and when i use route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0    U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0            UG    0      0        0 eth0

I don' know what i can do... 
Please help me! :confused:

---

### Post by rplantz on 2005-10-26
Have you tried restarting your router?

Every once in a while, my router seems to lose its way. Following the procedures in the manual for my router, I turn it off, wait a minute or so, then turn it back on. The router takes about a minute to reboot itself, and I'm back in business.

Bob

---

### Post by BlackWingAngel on 2005-10-26
thanks a lot but it doesn't work... i've tried configurating for DHCP server too.. but when i ping the router the result is the same... with WinXP and 2000 the ping (i've other 2 pc connected to this router) works perfectly... 
help!!!! i'm going crazy!!!

---

### Post by mips on 2005-10-26
Please post the following info in this thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you subscribing to from them
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)

Please provide links where possible to the above questions.

---

### Post by mips on 2005-10-26
[QUOTE=BlackWingAngel]thanks a lot but it doesn't work... i've tried configurating for DHCP server too.. but when i ping the router the result is the same... with WinXP and 2000 the ping (i've other 2 pc connected to this router) works perfectly... 
help!!!! i'm going crazy!!![/QUOTE]

What is wrong with the above ping results ???

---

### Post by wylfing on 2005-10-26
Hold on, here. The OP's ping and route results are normal. This is not a router problem, and it is not an ethernet adapter problem. The interface and the router are working fine.

When you say you "can't connect to the internet" what exactly are you doing? Have you tried pinging internet hosts using their IP numbers? Try pinging Google at 68.115.71.53.

edit:
> What is wrong with the above ping results ???
Nothing, as far as I can see.

---

### Post by mips on 2005-10-26
It's most likely a DNS issue.

---

### Post by BlackWingAngel on 2005-10-26
well.. thaks to everyone :)
a) router D-Link DSL-G604T(also access point wireless and adsl modem)
b)I bought it
c)the pc where I have ubuntu is connected to the router by a ethernet cable
d)there isn'bridgefilters
e)i live in italy
f)my provider is Telecom
g)"always connected" contract for ADSL 1.5 mps
h)router configuration:
dhcp configuration: start address 192.168.1.2
                           end address 192.168.1.254
                          primary DNS:192.168.1.1 (the router's IP)

DNS configuration:  DNS Relay Selection = Use autodiscovered DNS only
                          	Preferred DNS Server: 139.175.55.224

Management IP configuration:IP Address : 192.168.1.1
                                        NetMask: 255.255.255.0
                                        Default: Gateway 192.168.100.1
                                        Hostname: mygateway(this is the real name)
                                        Domainname: ar7
connection type: PPPoA, encapsulation:VC, modulation type:MMODE

the pc configuration is for DHCP.. on Network i've set the option for it and ifconfig confirm that the ethernet controller works

i've tried with ping [www.tiscali.com](www.tiscali.com).. but i didn't have a result and when i try to go on google web site with firefox i don't see anything

---

### Post by Wobble on 2005-10-26
This sounds like the same problem i have. I can successfully ping the router at 192.168.1.1 and i can ping [www.google.com](www.google.com) using the name (rather than the IP address) however, Firefox doesn't appear to be able to connect to the network at all.

The proxy settings in Firefox say "direct connection to internet".

Any help greatly appreciated.

Ian

---

### Post by BlackWingAngel on 2005-10-26
Wobbie when i ping the router or the google site i don't have any response.. but it seems the sames problem(but firefox don't give me any response)
i'm VERY going crazy!!! :confused:

---

### Post by herot on 2005-10-26
blackwing, do ```
ifconfig
``` and post it please...

---

### Post by BlackWingAngel on 2005-10-26
ifconfig eth0 this is the result:

eth0 Link encap:Ethernet HWaddr 00:11:2F:5B:AB:95
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:2fff:fe5b:ab95/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:932 errors:0 dropped:0 overruns:0 frame:0
TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:68391 (66.7 KiB) TX bytes:17800 (17.3 KiB)
Interrupt:17 

it was at the beginning of the tread ;)

---

### Post by herot on 2005-10-26
i dont know why firefox wouldn't be working then perhaps try installing another browser and trying that, i mean since you can ping internal AND external there really should be no reason you couldn't browse...

---

### Post by herot on 2005-10-26
im sorry BlackWingAngel... i keep getting you confused with wobble...
your problem seems to be that your cable/DSL modem isn't getting a connection to your telco... OR that your cable/DSL modem isn't talking to your router...
check your settings and cables on both ...  there are usually web interfaces for checking these settings and i am assuming that you know how... if not i shall try to explain further...
also... if you can try bypassing the router and plugging straight from cable/DSL modem into your ethernet port

---

### Post by BlackWingAngel on 2005-10-26
Maybe i don't explain well... when i try to ping the router or another site like google the ping doesn't work.. for example when i do:
ping 192.168.1.1(the router IP) this is the result:

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.715 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.685 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.685 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.692 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.691 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.682 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.679 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.677 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.688 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.676 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.682 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.684 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=255 time=0.690 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=0.683 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=0.671 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=0.678 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=0.684 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=255 time=0.686 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=255 time=0.682 ms

infinite times!!
or when i try to ping [www.google.com](www.google.com) it it doesn't give me a result..... :°°°(

---

### Post by BlackWingAngel on 2005-10-26
the modem,the router and the cable works because i have a dual boot on this pc and under Win the internet connection go very well

---

### Post by EggMan on 2005-10-26
the endless pinging of the router means that Ubuntu can see it so the problem lies in DNS
Im not sure on how to change your nameservers but someone will know.

PS: Try  " ping 64.233.161.99 -c 4 "  That should make you ping google 4 times, if that doesnt work then you cant see the internet if it works then you have a DNS problem

---

### Post by herot on 2005-10-26
my ping times to my wireless router are even slower than yours...
what ping times do you get when you are in windows...???
```

herot@slasheru:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.20 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.30 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.995 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=1.41 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=1.06 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=1.04 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1.02 ms

```

---

### Post by BlackWingAngel on 2005-10-26
thanks eggman if i try "ping 64.233.161.99 -c 4 " it says me that 4 packets trasmetted 0 recived. and if i do "ping 192.168.1.1(the router) -c 4" it says 4 packet trasmitted and 4 recived.
Do I have problems with DNS?

---

### Post by EggMan on 2005-10-26
hmmm try someother ipaddress that are out there like these , the google one got messed somehow 
```
 66.208.104.76 66.208.107.51 
```

---

### Post by BlackWingAngel on 2005-10-26
these are good... if i ping these addresses the result is 4 packets trasmitted 4 recived.... 
i don't understand it... :confused:

---

### Post by EggMan on 2005-10-26
well that means the your DNS is messed up, so someone will have to help you with that, as i dont know how and im havign my own problems with Ubuntu and my network ([http://ubuntuforums.org/showthread.php?t=61689](http://ubuntuforums.org/showthread.php?t=61689)) <bump>

---

### Post by BlackWingAngel on 2005-10-26
thanks very mutch eggman :) ... someone else can give me an answer how i can   resolve it??

---

### Post by EggMan on 2005-10-26
Ok can you post you /etc/resvol.conf here so that we can tell you what to add.  
kkzthx ;)

---

### Post by mips on 2005-10-28
[QUOTE=BlackWingAngel]thanks very mutch eggman :) ... someone else can give me an answer how i can   resolve it??[/QUOTE]

Have a look at my post in this thread (4th post down) as your problem seems similair:
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by mips on 2005-11-01
What was the outcome ?

---

### Post by dov_s on 2005-11-01
You should add to /etc/resvol.conf yours ISP DNS IP address.
If you dont know that ask your ISP help desk.:KS

---

### Post by SlasherMCT on 2006-02-13
I have just fixed the problems I had by updating the firmware on my DLINK DSL-G604T to the V1.00B02T02.UK.20050815 release if anyone else has this problem and ADSL modem...

---

### Post by naurus on 2007-08-23
the problem with firefox could be IPv6...

in firefox type "about:config" and then use the filter bar to search "6" and make sure the option "network.dns.disableIPv6" is true. if that doesn't work, try changing it to false.

hope that helps,
naurus

---

### Post by naurus on 2007-08-23
oops, i should've looked at the date on this topic ](*,)

---

