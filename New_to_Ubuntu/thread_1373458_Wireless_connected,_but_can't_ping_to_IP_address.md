---
title: "Wireless connected, but can't ping to IP address"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by marcusesses on 2010-01-05
Hi all,

Like the title says, wicd says I'm connected, but I can't send or receive packets, and I can't browse the webbernet. 

Some commands:

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:10:7a:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 B)  TX bytes:340 (340.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:00:97:e4  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::21c:bfff:fe00:97e4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:4074 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1742 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:207553 (207.5 KB)  TX bytes:177592 (177.5 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-00-97-E4-30-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

04:00.0

```

lspci | grep Network

```

 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 

```


iwconfig
```

lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abg  ESSID:"CK"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:56:38:25:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-37 dBm  Noise level=-127 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I had previously had similar problems with the wireless, as noted here ([http://ubuntuforums.org/showthread.php?t=1306413](http://ubuntuforums.org/showthread.php?t=1306413)), but that solution doesn't appear to work anymore, as I can connect, just not do anything else.

I was also using a different wireless network than the one I am currently using for the past two weeks. When I returned to my old network, I ran into these problems. I'm not sure what would have caused this, but any help is appreciated.

---

### Post by RedSingularity on 2010-01-05
What happens when you ping something like google?

ping -c 5 [www.google.com](www.google.com)

---

### Post by mikewhatever on 2010-01-05
By pinging an IP, do you mean pinging you router, for example, 192.168.1.0, or pinging a URL, like [www.google.com?](www.google.com?)
Can you ping your router?
Can you ping 216.239.59.99?
How about 217.0.0.1?

---

### Post by gradinaruvasile on 2010-01-05
Run

ip rou

in a terminal. What gives?

---

### Post by marcusesses on 2010-01-05
> **RedSingularity said:**
> What happens when you ping something like google?

ping -c 5 [www.google.com](www.google.com)

```
ping unkown host google.com
```

> **mikewhatever said:**
> By pinging an IP, do you mean pinging you router, for example, 192.168.1.0, or pinging a URL, like [www.google.com?](www.google.com?)
Can you ping your router?
Can you ping 216.239.59.99?
How about 217.0.0.1?

When I ping the router, it is very slow, and there is a 100% packet loss.

When I ping the other two, it works fine (transmits and receives signals).

> **gradinaruvasile said:**
> Run

ip rou

in a terminal. What gives?

```
192.168.2.0/24 dev wlan0 proto kernel scope link src 192.168.2.13

169.254.0.0/16 dev wlan0 scope link

default via 192.168.2.1 dev wlan0
```

---

### Post by RedSingularity on 2010-01-05
Can you ping your router?

ping -c 5 192.168.1.1

---

### Post by marcusesses on 2010-01-05
> **RedSingularity said:**
> Can you ping your router?

ping -c 5 192.168.1.1

Here are the statistics when I do that

```
5 Packets transmitted,0 received, 100% packet loss, time 4031ms 
```

---

### Post by mikewhatever on 2010-01-06
> **marcusesses said:**
> 


When I ping the router, it is very slow, and there is a 100% packet loss.

When I ping the other two, it works fine (transmits and receives signals).





That is odd. Are you sure you are pinging the right IP? Your router appears to be 192.168.2.1.

---

### Post by marcusesses on 2010-01-06
> **mikewhatever said:**
> That is odd. Are you sure you are pinging the right IP? Your router appears to be 192.168.2.1.

Well when I ping that IP, it seems to work. So I guess I can ping my router, but not anything else?

---

### Post by gradinaruvasile on 2010-01-06
Ping 192.168.2.1, that is your gateway.
Is that working?

Also, do a 

cat /etc/resolv.conf

What gives?

---

### Post by gradinaruvasile on 2010-01-06
> **marcusesses said:**
> 

When I ping the other two, it works fine (transmits and receives signals).



Dude, 216.239.59.99, the IP suggested by mikewhatever IS Google. 
And your router is 192.168.[COLOR="Red"]2.1[/COLOR] that seems to respond.
So you have a DNS problem.

The DNS servers are in the  /etc/resolv.conf file. As i said in the previous post, look at the file (cat /etc/resolv.conf) to see whats wrong.

---

### Post by mikewhatever on 2010-01-06
> **marcusesses said:**
> Well when I ping that IP, it seems to work. So I guess I can ping my router, but not anything else?

Well, as said, you can pig yourself, your router and google.com, which suggests you can probably ping anything else. Make sure your wireless setting in the network manager have 192.168.2.1 in place of DNS server.

---

### Post by marcusesses on 2010-01-06
Ok, it works...for now.
The output of cat /etc/resolv.conf is

```
domain vscysk.yourlink.ca
search vscysk.yourlink.ca
nameserver 66.128.93.30
nameserver 66.128.93.31
```

In my network manager (wicd), I changed to a static DNS, and used 192.168.2.1 as the DNS, which got things working.

I'm not sure if this is s permanent solution though. Can someone explain what the problem was to me? Does it have something to do with the fact that I started using a new wireless network? Also, why would I be able to ping to the IP of google, but when using the google domain name?

Thanks for your help, and hopefully I can avoid silly problems like this in the future.

---

### Post by gradinaruvasile on 2010-01-06
> **marcusesses said:**
> Ok, it works...for now.
The output of cat /etc/resolv.conf is

```
domain vscysk.yourlink.ca
search vscysk.yourlink.ca
nameserver 66.128.93.30
nameserver 66.128.93.31
```

In my network manager (wicd), I changed to a static DNS, and used 192.168.2.1 as the DNS, which got things working.

I'm not sure if this is s permanent solution though. Can someone explain what the problem was to me? Does it have something to do with the fact that I started using a new wireless network? Also, why would I be able to ping to the IP of google, but when using the google domain name?

Thanks for your help, and hopefully I can avoid silly problems like this in the future.

Its a good solution. You can assign static IP addresses to your connection (best bet is the same your router gives you with DHCP), manual DNS's etc. I do have static IP address of my wireless connections at home and at work.

The DNS is the abbreviation of Domain Name System. This is a connection to a server that can fetch the IP addresses of domains (example [www.google.com](www.google.com)) you ask them. The communication of actual data is done between IP addresses only. You can navigate the web without DNS, but you will have to know every servers IP address.

I dont know why it happened, but your router that should asssign DNS addresses. Maybe Wicd retained the other network's DNS? I use 3 networks with Wicd and have no problems. 
The latest Wicd versions can be installed by adding the following line to /etc/apt/sources.list:

deb [http://apt.wicd.net](http://apt.wicd.net) karmic extras

Currently its at version 1.6.2.2

---

