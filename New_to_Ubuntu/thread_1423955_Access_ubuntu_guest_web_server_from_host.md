---
title: "Access ubuntu guest web server from host"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by kkarad on 2010-03-07
VM: VMWare Fusion
Host: Mac OS Snow Leopard
Guest: Ubuntu 9.10

Hi, 
I have set up a web server listening to port 8080 but I cannot access it from host. I tried different network modes (NAT, Bridged) but had no success.

What's the Ubuntu configuration I need to change so that I can make guest web server available to host?

These are the actions I did so far (in guest ubuntu machine using bridged mode)?

0. Make sure that the web server is available from the guest machine itself (success)
```
http://localhost:8080/apex
```
1. Disable the Firewall to test the connection with no interference:
```

kostas@ubuntu:~$ sudo ufw disable
Firewall stopped and disabled on system startup
kostas@ubuntu:~$ sudo ufw status
Status: inactive

```
2. Run ifconfig to get the IP address of the guest machine
```
kostas@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:56:af:80  
          inet addr:**192.168.1.85 ** Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe56:af80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3118 (3.1 KB)  TX bytes:4971 (4.9 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6075 (6.0 KB)  TX bytes:6075 (6.0 KB)

```
3. Connect to the web server from the host machine (no success):
```
http://192.168.1.85:8080/apex
```


Thank you in advance,
Kostas

---

### Post by kkarad on 2010-03-07
Hi guys,

I found the problem!

... I checked the darkstat network traffic monitor (in ubuntu) and I discovered that my host http requests are received by the ubuntu guest.
 
The culprit was the actual web server. Its an internal oracle-xe web server for database administration. There is an option to enable non local http requests which i enable and the problem solved.


Thanks for you help

---

