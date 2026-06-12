---
title: "[SOLVED] help my tower wont connect to the internet"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by minispalla on 2008-05-11
i have been having problems connecting to the internet with my tower that is running ubuntu 8.04 , its connected via Ethernet to my wrt54g which when i connect my laptop to the router via a Ethernet cable it works just fine but when i connect my tower that is running ubuntu it wont work ( but if i boot into windows ( i know odd ) the internet works just fine ( thats the same computer)) 

here is the output of a bunch of stuff tell me if you need more i will be happy to fetch it 

spalla@spalla-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:2c:0a:4c:cf  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe0a:4ccf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:416 (416.0 B)  TX bytes:1118 (1.0 KB)
          Interrupt:16 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:203700 (198.9 KB)  TX bytes:203700 (198.9 KB)

spalla@spalla-desktop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
spalla@spalla-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
246 packets transmitted, 0 received, 100% packet loss, time 245009ms

spalla@spalla-desktop:~$ 
spalla@spalla-desktop:~$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

spalla@spalla-desktop:~$ 

i am also using the opendns servers if that helps 

i have no idea were to go from here

---

### Post by minispalla on 2008-05-11
*bump

---

### Post by vorgusa on 2008-05-11
hmm the error for the nslookup makes it seem like you do not have dns set up properly.  Try doing an nslookup on a working computer for google and then ping that IP address on your Ubuntu 8.04 tower to see if you can ping a regular IP... if that works then you just need to find your DNS server from a working computer and set that on your Tower


ohh yeah also try pinging 192.168.1.1, which is your router.. if that works you know your card is working, and since you have a default gateway and you know your router is working, that should be a pretty good sign it is DNS

---

### Post by minispalla on 2008-05-11
i tried pinging the 208.67.222.222 (opendns's DNS) 
but that didnt work, but if i go to firefox and i type [http://64.233.167.99/](http://64.233.167.99/) for the address it goes strait to the google home page but if i try to ping that address it doesnt work ? 


any other ideas ?

---

### Post by vorgusa on 2008-05-11
right click the Network Manager icon at the top right of your screen and go to Connection Information and tell me what you see..  Just because you can not ping something does not mean it is not there.. some sites block pings so it just drops.

---

### Post by minispalla on 2008-05-11
oh i didnt know that and it says this 

interface:Ethernet (eth0)
speed: 100mb/s 
driver: via-velocity 

ip address: 192.168.1.101
broadcast address 192.168.1.255
subnet mask 255.255.255.0
default route 192.168.1.1
primary dns 208.67.222.222
secondary dns 208.67.220.220
hardware address 00:50:2C:0A:4C:CF 

is it possible there is some kind of firewall 
i already uninstalled that ufw a while ago is there anything else like that ?

---

### Post by minispalla on 2008-05-11
*bump

---

### Post by minispalla on 2008-05-12
*bump

---

### Post by chili555 on 2008-05-12
Although you have an IP address associated with your interface, eth0, you are not actually connected to the router:```
--- 192.168.1.1 ping statistics ---
246 packets transmitted, 0 received, 100% packet loss, time 245009ms
```By the way, if it won't reply in 3-4 pings, it sure won't do so in 246. You can control the number of pings by specifying the count:```
ping -c3 192,168.1.1
```I suggest removing all the data here:> ip address: 192.168.1.101
broadcast address 192.168.1.255
subnet mask 255.255.255.0
default route 192.168.1.1
primary dns 208.67.222.222
secondary dns 208.67.220.220
hardware address 00:50:2C:0A:4C:CF
and specifying DHCP. The problem I have with static IP addresses, when you are troubleshooting, is that when you are not connected, you have an IP address; when you *are* connected, you have an IP address. With DHCP, you only get an IP address when you connect. When you have everything set to DHCP, then do:```
sudo dhclient eth0
```Let us know if you connect or time out. If you need a static IP address for some other reason, let's address that once we actually connect.

---

### Post by minispalla on 2008-05-12
alright this is what i got 
spalla@spalla-desktop:~$ sudo dhclient eth0
[sudo] password for spalla: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:2c:0a:4c:cf
Sending on   LPF/eth0/00:50:2c:0a:4c:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 42457 seconds.
spalla@spalla-desktop:~$ 

and the internet still doesn't work

---

### Post by vorgusa on 2008-05-12
Try checking the physical parts, such as the cable, lights on the router, and port...  Try each of these to see if one gives us new info

1. Look at the port where the cable is plugged in to see if there are lights on both the router and the computer.

2.Move the cable to a different port and test to see if it works.

3. Try a new cable and see if it works.

If all of these work fine try taking the cable from your modem and plug it directly into your computer then restart the modem and wait a couple min then test to see if it works.

---

