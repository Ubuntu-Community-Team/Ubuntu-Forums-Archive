---
title: "[SOLVED] Can't access computer through ssh"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by morty35 on 2008-11-11
I have a friend and business partner that is working with me on a project.  I sometimes need to access his files and he needs to access mine.  We have tried to use ssh (we both have openssh-server installed), but whenever I try to use this command it just lags.

$ ssh username@ipaddress

He says the same thing happens when he tries to access my machine.  I am guessing that it might be the firewall or not being able to access the localhost behind the service provider or router.  

Here is my ifconfig readout (I have a dynamic address so it changes):
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:08:2e:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:c9:08:2e:0e  
          inet addr:169.254.2.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144112680 (137.4 MB)  TX bytes:144112680 (137.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:73:85:cb  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe73:85cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12903178 (12.3 MB)  TX bytes:2375081 (2.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-73-85-CB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I am using a laptop with wireless.  How do I ssh into his machine?

---

### Post by dmizer on 2008-11-11
What do you mean by "it just lags"? Do you get a connection at all?

Are you actually on the same network as your business partner? If not, then at least one of you will need to set up port forwarding on your router.

---

### Post by cariboo on 2008-11-11
If both of you are behind routers have port forwarded to port 22 from your computer to the router?

To check go to [canyouseeme]("http:///www.canyouseeme.org/") and make sure port 22 or whatever port you setup for ssh is open.

Jim

---

### Post by phantomgunex on 2008-11-11
Did you port forward port 22 and make sure that the ssh daemon is already running

---

### Post by morty35 on 2008-11-11
How do you forward port 22.  I am not sure I know what that is.  I am guessing that my ipaddress is hidden behind the router.  Is port forwarding allowing access to others to my ipaddress through the router?  Also, how do I find out the ipaddress of my router or internet service provider?  
 
Sorry, I just don't know that much about networking.

---

### Post by dmizer on 2008-11-11
> **morty35 said:**
> How do you forward port 22.  I am not sure I know what that is.  I am guessing that my ipaddress is hidden behind the router.  Is port forwarding allowing access to others to my ipaddress through the router?  Also, how do I find out the ipaddress of my router or internet service provider?  
 
Sorry, I just don't know that much about networking.

There is a lot of good information about port forwarding on this page: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

To find your external IP address, browse to [www.whatismyip.com](www.whatismyip.com)

---

