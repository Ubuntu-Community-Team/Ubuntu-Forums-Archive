---
title: "Network Connection"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by a1tone on 2007-05-22
Hi

I have a D-Link Router and have my Laptop connected via Wireless Connection. I also have a Desktop PC and I am trying to connect this to the Internet.

The OS is Ubuntu and I am unsure how to configure this. The Desktop PC didn't have a Ethenet Connector so I installed a Internal Ethernet Network Card. I have connected the computer to the router using the RJ45.

How do I configure the network so both PC's can use the same broadband.

Thanks in advance.

---

### Post by ugm6hr on 2007-05-22
Having seen your post, I have made the following assumptions:
[I]your Dlink router is a wireless ADSL router (or is a router connected to a DSL modem);
you have broadband which is connected via the Dlink router;
you can already connect to the internet from your wireless laptop (via your Dlink router)
you are using a recent Ubuntu version on the desktop[/I]

If this is true, then simply connecting the desktop ethernet connector (from your new Network Card) to the Dlink router's RJ45 ethernet connector with the correct cable (i.e. standard patch cable - not a cross-over cable) should allow you to connect to the same broadband from the desktop.  It will have no adverse effect on the wireless connection.

---

### Post by a1tone on 2007-05-22
You assumptions were correct.

I have connected the computer to the router, but when I use Firefox to connect to the net, the message displayed is:

Server not found

Firefox can't find the server at [www.google.co.uk](www.google.co.uk)

I have also tied this with ebay and a few other sites, but the same problem occures.

Thanks

Anthony

---

### Post by ugm6hr on 2007-05-22
Couple of things to consider:
1. Enter in the web address of firefox: 192.168.0.1 (or whatever your router IP is - it might be 192.168.1.1 for Dlink) - does it connect to the router setup page?
2. In the network settings, try with a. "roaming enabled" or b. disabled with DHCP.

---

### Post by NumPy on 2007-05-22
Again assuming you are trying to connect via the PC:
Open a terminal and see if you are getting an IP address is the first step

Type the following comman:
```
# ifconfig
```

It will show several connections. Typically the one you want IF you only have ONE ethernet card installed is:eth0 

ifconfig will report the IP address, subnet mask and default gateway, which is all sent from your router. (see below)
```
th0      Link encap:Ethernet  HWaddr 00:11:5B:45:E0:E0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe200 

eth1      Link encap:Ethernet  HWaddr 00:12:17:5A:3D:BA  
         ** inet addr:10.136.181.4  Bcast:10.136.181.255  Mask:255.255.255.0**
          inet6 addr: fe80::212:17ff:fe5a:3dba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:614125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:447803055 (427.0 MiB)  TX bytes:259783408 (247.7 MiB)
          Interrupt:19 Base address:0xe900 

eth0:avah Link encap:Ethernet  HWaddr 00:11:5B:45:E0:E0  
          inet addr:169.254.9.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1815334 (1.7 MiB)  TX bytes:1815334 (1.7 MiB)

```
After having tested this, try a restart of the system and then repeat the process above. 
As well, making sure you router is using/sending DHCP is a great step, restart it as well. 

Cheers
~NumPy

---

### Post by a1tone on 2007-05-23
> **ugm6hr said:**
> Couple of things to consider:
1. Enter in the web address of firefox: 192.168.0.1 (or whatever your router IP is - it might be 192.168.1.1 for Dlink) - does it connect to the router setup page?
2. In the network settings, try with a. "roaming enabled" or b. disabled with DHCP.

1. Tried to enter the setup page address, but it dosen't connect.
2. Tried both of rhese, but nothing.

---

### Post by a1tone on 2007-05-23
> **NumPy said:**
> Again assuming you are trying to connect via the PC:
Open a terminal and see if you are getting an IP address is the first step

Type the following comman:
```
# ifconfig
```

It will show several connections. Typically the one you want IF you only have ONE ethernet card installed is:eth0 

ifconfig will report the IP address, subnet mask and default gateway, which is all sent from your router. (see below)
```
th0      Link encap:Ethernet  HWaddr 00:11:5B:45:E0:E0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe200 

eth1      Link encap:Ethernet  HWaddr 00:12:17:5A:3D:BA  
         ** inet addr:10.136.181.4  Bcast:10.136.181.255  Mask:255.255.255.0**
          inet6 addr: fe80::212:17ff:fe5a:3dba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:614125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:447803055 (427.0 MiB)  TX bytes:259783408 (247.7 MiB)
          Interrupt:19 Base address:0xe900 

eth0:avah Link encap:Ethernet  HWaddr 00:11:5B:45:E0:E0  
          inet addr:169.254.9.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1815334 (1.7 MiB)  TX bytes:1815334 (1.7 MiB)

```
After having tested this, try a restart of the system and then repeat the process above. 
As well, making sure you router is using/sending DHCP is a great step, restart it as well. 

Cheers
~NumPy

Tried this also. It is displaying an eth0, but still can't connect.

---

### Post by ugm6hr on 2007-05-23
> **a1tone said:**
> Tried this also. It is displaying an eth0, but still can't connect.

What exactly does it say? Just cut and paste the Terminal output here.

---

### Post by a1tone on 2007-05-25
Here is the ifconfig read out. 

anthony@anthony-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:08:54:45:FE:81  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::208:54ff:fe45:fe81/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:9192 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2311 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:7167737 (6.8 MiB)  TX bytes:170967 (166.9 KiB) 
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b) 

anthony@anthony-desktop:~$

---

### Post by a1tone on 2007-05-25
I don't know what happened, but its started to work now.

---

### Post by NumPy on 2007-05-25
Good to hear :)

---

