---
title: "Can connect only to google websites Ubuntu 14.04 and bsnl broadband"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by Rajeev_Sebastian on 2014-07-03
I have recently upgraded to ubuntu 14.04 and have set up a dsl  configuration for my BSNL broadband connection.the problem is that i can  connect to Google owned websites like youtube or gmail.I can connect to  some other small sites as well.However i cant connect to most of the  other websites.I can ping dig and nslookup other websites though. I am a beginner to linux to  based systems.Can someone help me out here
```
IFCONFIG Response

rajeev@BE:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:ae:b4:30  
          inet6 addr: fe80::21d:baff:feae:b430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28800 (28.8 KB)  TX bytes:4375 (4.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:197277 (197.2 KB)  TX bytes:197277 (197.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:ed:9d:0e  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:feed:9d0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46586064 (46.5 MB)  TX bytes:3480601 (3.4 MB)
```

NSLOOKUP for google.com and facebook.com(cant browse)
```
rajeev@BE:~$ nslookup google.com
  Server:       127.0.1.1
  Address:  127.0.1.1#53

  Non-authoritative answer:
  Name: google.com
  Address: 74.125.130.102
  Name: google.com
  Address: 74.125.130.101
  Name: google.com
  Address: 74.125.130.100
  Name: google.com
  Address: 74.125.130.139
  Name: google.com
  Address: 74.125.130.113
  Name: google.com
  Address: 74.125.130.138

  rajeev@BE:~$ nslookup facebook.com
  Server:       127.0.1.1
  Address:  127.0.1.1#53

  Non-authoritative answer:
  Name: facebook.com
  Address: 173.252.110.27

  rajeev@BE:~$ 
```

---

### Post by TheFu on 2014-07-03
Use standard network troubleshooting techniques to determine the exact problem. This isn't OS specific.
[http://ubuntuforums.org/showthread.php?t=2187392](http://ubuntuforums.org/showthread.php?t=2187392) has links that should help. Pay careful attention to the Networking 101 link.

---

### Post by grahammechanical on 2014-07-03
Do you see the words: UP BROADCAST RUNNING MULTICAST? You have that for both ethernet (wired connection) and wlan (wireless connection). This means the the two network adapters are functioning and that Ubuntu has drivers for each of them and that Network Manager is connected to the router. And as you say, the router is connecting to the Internet. This is shown by the numbers for RX (Receiving) and TX (Transmitting).

Routers have firewalls. Is the firewall in the router limiting connection to certain websites? Has the firewall in Ubuntu been activated and restricting access to certain web sites? What error messages do you see when you try to access web sites?

Regards.

---

### Post by Rajeev_Sebastian on 2014-07-04
@TheFu:Thank you for the links ill definitely check them out
@grahammechanical:Thank you for replying.dont know if this helps at all but the modem works fine in windows.Also how should i check for firewalls

---

### Post by TheFu on 2014-07-04
To check a firewall on a router, you'll need to login to the router and use those tools.
On Linux, run **sudo iptables -L** - all programs that claim to be firewalls on Linux are really just an interface to iptables. It is the "system of record" for all the rules, so that command will ask it.

BTW - if there are 2 network interfaces active and both have a gateway, then confusion can happen.  It is best for non-experts to only have 1 NIC active at a time.

Also - many of the network tools are becoming depricated.  nslookup is one of those.  As IPv6 takes over, it will be important to use the newest tools, since IPv4 tools won't work.  I'm not ready for IPv6 here, so I disable it on all hardware and completely block it in my firewalls to prevent unauthorized traffic by rogue users.

---

### Post by Rajeev_Sebastian on 2014-07-04
Output tha i recieved

rajeev@BE:~$ sudo iptables -L
[sudo] password for rajeev: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Rajeev_Sebastian on 2014-07-04
should i also disable ipv6 on my computer
@grahammechanical : the error i recieve is  connection timed out on firefox
ping gives around 80 ms for google sites  while sites like fb yahoo take around 260-270 ms as RTT

---

