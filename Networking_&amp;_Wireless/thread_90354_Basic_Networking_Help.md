---
title: "Basic Networking Help"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by N8K99 on 2005-11-14
I am having trouble networking my computers together. First of all, I'm trying to use a Linksys BEFSR41 router to connect my Gateway running Enlightened Ubuntu 5.10 with my Powerbook running OS X 10.3.9. I can get either computer to connect to my DSL modem individually. I can get either computer to connect through the router, individually, but I can not get them both to connect at the same time through the router. I have not been able to set the WAN IP Address on the router. When I try to go to 192.168.1.1 my browser does not find the address. I RTFMed for the router, but it is useless unless I run some flavor of MSWindows. If some one can helop with this probelm, I'd be grateful.:smile: 


BTW I also have a Toshiba Tecra 500CDT running Hoary that I can not get the Creditcard Bus to be seen, even though it is listed in the supported hardware.:confused: 

Thank you

---

### Post by dbott67 on 2005-11-14
Could you please provide a few details about your ISP and setup, such as:
1. Is your ISP cable or DSL?
2. Are your computers are wired or wireless?
3. Are your computers configured for DHCP or static IP addresses?
4. What are the assigned IP addresses and gateways for each computer? Post the output of 'ifconfig' and 'route' here:
```
dbott@breezy:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:147268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13356338 (12.7 MiB)  TX bytes:13356338 (12.7 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:B8:EB:74
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:feb8:eb74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15107 errors:8 dropped:0 overruns:0 frame:0
          TX packets:17768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10981913 (10.4 MiB)  TX bytes:3287908 (3.1 MiB)
          Interrupt:11 Base address:0x4000

dbott@breezy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```
In my case, my IP address is 192.168.1.100 and gateway is 192.168.1.1.

-Dave

---

### Post by N8K99 on 2005-11-15
Sorry for the thread. After I posted I saw the  Sticky Thread about Troubleshooting Wired Ethernet. Following the directions within that post, I was able to connect both computers to the internet simultaneously. 

Basically my probelm was solved once I ran [SIZE="1"]sudo dhclient eth0[/SIZE] and was able to access [SIZE="1"]192.168.1.1[/SIZE] through Firefox and complete the configuration process of the wired router. The Powerbook took a little bit of work to get online- perhaps the socket I had the cable plugged into does not work and hence the really low price on ebay (<$10 US with shipping). :cool: 

Now, I am going to have to learn how to share between these computers, if that is possible.

---

### Post by N8K99 on 2005-12-06
Oh yes, I have got the two computers to be synergized together, using synergy of course. I have other items which I am dealing with, but still have a third computer with a Xircom CreditCard Bus that I need to get connected to the Network. I can not get the OS to recognize the PCMCIA card. I need a command line instrcution to give the computer and I don't know what it is.

---

