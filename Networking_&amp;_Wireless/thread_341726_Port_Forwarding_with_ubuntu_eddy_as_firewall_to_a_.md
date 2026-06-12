---
title: "Port Forwarding with ubuntu eddy as firewall to a lan machine"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by anieshuk on 2007-01-19
Hai all
I am new to ubuntu. Its really good to see such os.I face some problems with firewall configuration
in ubuntu. Can any one pleas help me?

Here are my questions?
1. [13:600] - A   what does these numbers mean
2. :OUTPUT ACCEPT[28:2004] - what does ":" mean here
3. How to make a simple port forwarding
my internet devie is ppp0 configured through eth3 and lan card in eth0 connected to other pC

Pls help me
Tks in advance
Aniesh U.K

---

### Post by darrenm on 2007-01-19
Hi. 

Which guide are you following to get these commands?

Also can you post the output of ```
ifconfig -a
```

---

### Post by anieshuk on 2007-01-19
hai
tks for the reponse
here is the list
eth0      Link encap:Ethernet  HWaddr 00:C1:26:08:27:A7  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c1:26ff:fe08:27a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:243260 (237.5 KiB)  TX bytes:708 (708.0 b)
          Interrupt:10 Base address:0xef00 

eth1      Link encap:Ethernet  HWaddr 00:07:95:50:9A:60  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd400 

eth3      Link encap:Ethernet  HWaddr 00:0B:2B:11:27:8C  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:2bff:fe11:278c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3147222 (3.0 MiB)  TX bytes:675522 (659.6 KiB)
          Interrupt:5 Base address:0xce00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4820 (4.7 KiB)  TX bytes:4820 (4.7 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.xxx.xxx.xxx  P-t-P:59.xxx.xxx.xx ARP MULTICAST  MTU:1492  Metric:1
          RX packets:5260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3003821 (2.8 MiB)  TX bytes:540273 (527.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

i use a adsl modem to connect to internet using eth3 and eth0 is connected to lan.
I want request to this linux machine to be redirected to a lan machine.
I do not use any tool.I manuall type the command. But forwarding is not happening.
THe example that is got is from web a simple output of iptables. I was unable to understand that. like :PREROUTING [0:0] - what does this : and 0:0 mean?

Thanks a lot
Aniesh U.K

---

### Post by darrenm on 2007-01-19
I've never seen iptables rules written like that. 

Try this guide: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

or just install firestarter and use the GUI on that while you get familiar with iptables.

---

### Post by anieshuk on 2007-01-19
hai
tks for the reply. I tried firestarter as well as guarddog. all INPUT , OUTPUT commands filtering
are working but forwarding is not happinng.
I want to forward a request to port 8003 in lan ?
How can i do that. I tried a lot of commands but forwarding is not happining.
Can u help me pls?

Have a great day.
Aniesh U.K

---

### Post by darrenm on 2007-01-19
I assume your forwarding is not working because you are trying to use ppp0 as eth3. You either have ppp0 or eth3 as the internet device, not both.

---

