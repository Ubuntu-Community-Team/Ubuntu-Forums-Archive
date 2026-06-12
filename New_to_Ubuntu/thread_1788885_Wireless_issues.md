---
title: "Wireless issues"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by artificialintelligence on 2011-06-23
Hi Guys, im a complete novice to ubuntu although im getting a better idea everyday of how awesome it is. Unfortunately ive got some wireless issues. I keep getting a 'cannot find server' message when i try to access anything but the homepage. First this would not work with the wireless connection at all but i used a wired connection and reset the wireless connection and i can get as far as the home page but no further. Im running ubuntu 11.04 on a sony vaio vgn-n31s. Im sure its a proxy setting thing but im a little clueless. Any help would be much appreciated!! Cheers

---

### Post by inameiname on 2011-06-23
From the information you've given, it sounds less like an Ubuntu issue, and more like a router/network one. Have you changed anything with it? Also, a way to greatly help narrow down the trouble is to remove any encryption in your wireless signal (if you don't already). For me, that helps heaps, as often the second I make it an unsecure network I suddenly can get through. And another way to test it is to run a Linux Live CD/USB and then try and get online that way.

Regardless, I know those suggestions don't address your issue specifically, but it really does help narrow down the trouble, and where its coming from. After that is greatly deduce, you can further look into any proxy or whatever else issues.

---

### Post by artificialintelligence on 2011-06-23
Thanks for your advice. I took down the encryption code and it still didnt work. Also i dont have the live cd as i installed ubuntu through windows. I have tried using another internet explorer (chromium instead of firefox) and im getting the same issue if that provides any more info :(

---

### Post by inameiname on 2011-06-23
Ah. Well it very well could be the OS then. How about downloading Ubuntu real quick and throwing it on a flash drive or disc if you can. That way you know for sure its the OS installed. And having trouble on multiple browsers would show its something in the settings.

---

### Post by gandaran on 2011-06-23
does wired internet work? and the wireless drivers? what wireless device/chipset does the laptop have?

---

### Post by smurphy_it on 2011-06-23
Sounds like networking or router issue.  Potential firewall as well.

You should start with something simple first.  In a terminal try the following:

```
sudo ifconfig -a
```

Note the IP address for your wired/wireless card.  Would I be correct in assuming you use DHCP ?  If so, you should of automatically received an IP address and a nameserver address for DNS lookups.

So, if you have an IP.. try this:

ping your_ip_here
ping gateway_ip
ping [www.google.com](www.google.com)

Replace "your_ip_here" with the IP address listed from the ifconfig -a.  The gateway IP (assumine you have a 255.255.255.0 netmask, would be the three octets the same ending in one.
Ex:  my ip = 192.168.1.80  my netmask = 255.255.255.0 so gateway would = 192.168.1.1

Post back you finds, and while you are at it post the contents of:
```
sudo cat /etc/resolv.conf
```

---

### Post by artificialintelligence on 2011-06-23
eth0      Link encap:Ethernet  HWaddr 00:1a:80:45:47:e1  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:fe45:47e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2699670 (2.6 MB)  TX bytes:208161 (208.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:45:d5:5e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe45:d55e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8017 (8.0 KB)

ip ping gives a long list of these

64 bytes from 192.168.1.254: icmp_req=146 ttl=64 time=0.749 ms
64 bytes from 192.168.1.254: icmp_req=147 ttl=64 time=0.766 ms
64 bytes from 192.168.1.254: icmp_req=148 ttl=64 time=0.786 ms
64 bytes from 192.168.1.254: icmp_req=149 ttl=64 time=0.765 ms
64 bytes from 192.168.1.254: icmp_req=150 ttl=64 time=0.735 ms
64 bytes from 192.168.1.254: icmp_req=151 ttl=64 time=0.768 ms
64 bytes from 192.168.1.254: icmp_req=152 ttl=64 time=0.751 ms
64 bytes from 192.168.1.254: icmp_req=153 ttl=64 time=0.764 ms

gateway png: From 192.168.1.79 icmp_seq=1 Destination Host Unreachable
From 192.168.1.79 icmp_seq=2 Destination Host Unreachable
From 192.168.1.79 icmp_seq=3 Destination Host Unreachable
From 192.168.1.79 icmp_seq=5 Destination Host Unreachable


google ping: 64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=32 ttl=49 time=33.8 ms


response to 
sudo cat /etc/resolv.conf 

# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.254

I hope i dd this all right, im sorry im a little out of my depth when it comes to more involved computer stuff

thanks a lot

---

### Post by smurphy_it on 2011-06-23
Looks a little strange.

Your IP = 192.168.1.79
Your Gateway = 192.168.1.1

So you should:

```
ping 192.168.1.79 -w 3
```
then ping the gateway
```
ping 192.168.1.1 -w 3
```
and finally ping google
```
ping www.google.com
```

From the looks of it, your nameserver is wrong.  The nameserver typically points to your router, so your resolv.conf should read:

domain home
search home
nameserver 192.168.1.1

if you need to edit the nameserver, do:
```
sudo nano /etc/resolv.conf
```
when done making the changes exit and save with Ctrl-x.

---

### Post by artificialintelligence on 2011-06-23
Thanks again for your help and patience

PING 192.168.1.79 (192.168.1.79) 56(84) bytes of data.
64 bytes from 192.168.1.79: icmp_req=1 ttl=64 time=0.069 ms
64 bytes from 192.168.1.79: icmp_req=2 ttl=64 time=0.056 ms
64 bytes from 192.168.1.79: icmp_req=3 ttl=64 time=0.051 ms
64 bytes from 192.168.1.79: icmp_req=4 ttl=64 time=0.054 ms

--- 192.168.1.79 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.051/0.057/0.069/0.010 ms

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

The google.com ping gives a long list of these:

me=34.0 ms
64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=31 ttl=49 time=33.7 ms
64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=32 ttl=49 time=35.3 ms
64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=33 ttl=49 time=35.9 ms
64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=34 ttl=49 time=33.9 ms
64 bytes from bru01m01-in-f147.1e100.net (209.85.147.147): icmp_req=35 ttl=49 time=34.1 ms


the nameserver read 192.168.1.254 so i changed it to 192.168.1.1


Thanks so much

---

### Post by smurphy_it on 2011-06-23
So test out your web browsing.  If it works, just tag this thread as solved (under thread tools).

Cheers;

---

### Post by artificialintelligence on 2011-06-23
unfortunately the problem persists. The wired connection works but i can only access the homepage on the wireless connection :(

---

### Post by artificialintelligence on 2011-06-23
Also the nameserver keeps changing back to .254

---

### Post by smurphy_it on 2011-06-23
As your wlan IP is on a different vlan, typically one would add a route.  However, the IP of your wlan is a little peculiar.

inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0

Try this command:

```
route add -net 10.42.43.0 netmask 255.255.255.0 gw wlan0
```

---

### Post by smurphy_it on 2011-06-23
.254 is the network broadcast.  As long as you can still ping a [www.google.com](www.google.com) don't worry about it.

---

### Post by smurphy_it on 2011-06-23
Is this your own router you are connecting to ?  If so, chances are you have the gateway set to 192.168.1.254.  I would suggest going into your wireless router settings and change the gateway from 192.168.1.254 to 192.168.1.1

---

### Post by artificialintelligence on 2011-06-23
got a response of 

nathan@ubuntu:~$ route add -net 10.42.43.0 netmask 255.255.255.0 gw wlan0
wlan0: Unknown host

thanks again for your time

---

### Post by smurphy_it on 2011-06-23
I believe this would be the correct one then.

```
route add -net 10.42.43.0 netmask 255.255.255.0 gw 192.168.1.1 dev wlan0
```

---

### Post by smurphy_it on 2011-06-23
I believe this would be the correct one then.

```
route add -net 10.42.43.0 netmask 255.255.255.0 gw 192.168.1.1 dev wlan0
```

You could make this a persistent static route, however, as this is for wireless (at your place I'll assume) you probably don't want to do that.  As it may cause some grief when you hook up wirelessly elsewhere.

Might just want to run that command by hand each time.  I'm sure there is probably a better way though.

---

### Post by artificialintelligence on 2011-06-23
nathan@ubuntu:~$ route add -net 10.42.43.0 netmask 255.255.255.0 gw 192.168.1.1 dev wlan0


Im currently at my rented uni home but will be going home tomorrow, is it worth just giving up for now and trying my wireless at home?

---

