---
title: "lost my internet connection"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by skovy on 2009-04-15
i recently set up a new computer with ubuntu 8.10 and figured that it would be easy to set up a wireless connection, then i found out that i couldn't just pop it in and go.  so i took the computer to my parents house, and hooked up through a hard connection, downloaded all the updates that showed up, along with wine and firestarter.  it said i needed to restart, so after the restart i have no connection.  it says eth0 cannot be found on the firestarter.  im not real sure what i should look under as most posts just assume that you have access to that and tell you where to go from there.

---

### Post by jbrown96 on 2009-04-15
When you hook up the ethernet, what does the network manager icon say? Make sure that networking is enabled (right click on it). 

Go to a terminal (apps-->acc) and post the output of the following to help us better understand what's happening

```
lspci| grep Network
``` ```
ifconfig
``` ```
iwconfig
```
```
sudo dhclient
```

---

### Post by skovy on 2009-04-15
ted@ted-desktop:~$ lspci| grep network
ted@ted-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:b6:92:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:19355531 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:744 (744.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ted@ted-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ted@ted-desktop:~$ sudo dhclient
[sudo] password for ted: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/6a:b8:37:e6:1c:fb
Sending on   LPF/pan0/6a:b8:37:e6:1c:fb
Listening on LPF/eth0/00:19:66:b6:92:2a
Sending on   LPF/eth0/00:19:66:b6:92:2a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ted@ted-desktop:~$ 

the problem with the wireless is from the fact that i havent been able to find the drivers for the belkin f5d8053, i was hoping to install wine and be able to get it from that, but its not looking good.  there was a post under the wireless section of these forums about someone else having the same problem, the install.inf is different from the driver.inf or that is atleast what they are saying. 

thanks for the help

---

