---
title: "[SOLVED] Need help with ADSL wireless connection"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by ilych on 2008-04-19
Hello,

I'm not good with computers, so bear with me...

I connect wirelessly to a router which is connected to the Internet. In Windows, the wireless connection is called "GW-AP11X". The speed  is 11.0 MBPS and the status is "Limited or no connectivity", which doesn't matter. I then create a new broadband connection, enter in the username and  pw my ISP gave me, and I can connect to the Internet..

Now the first thing that is different in Ubuntu is that although it picks up the "GW-AP11X" connection, it never connects to it. I first tried

```
sudo pppoeconf
```

in Fluxbox (I have nm-applet and gnome-keyring-daemon on startup) but that failed altogether:
"Sorry, I scanned two interfaces, but the Access Concentrator  of your provider did not respond"

In GNOME, I tried sudo pppoeconf, and it worked. That is, I was able to enter my username and password. Also, in GNOME, it picked  up four interfaces but in fluxbox only two. Now, even though pppoeconf is working, I am not connected to the Internet. Here is my ifconfig -a and sudo dhclient (what does this do?)

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1015 (1015.0 b)  TX bytes:11622 (11.3 KB)
          Interrupt:3 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          inet addr:169.254.5.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

eth1:avah Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          inet addr:169.254.6.239  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3602 (3.5 KB)  TX bytes:3602 (3.5 KB)
```

```
$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6068
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:31:a3:d8:3c
Sending on   LPF/eth1/00:17:31:a3:d8:3c
Listening on LPF/eth0/00:15:c5:24:58:67
Sending on   LPF/eth0/00:15:c5:24:58:67
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

The weird part is this. I kept trying to connect to the "GW-AP11X" wireless connection (because I think that's where the problem is). And while it was connecting, at some points, I was able to connect to the Internet. But this was only for a short period of time and of course it died once it stopped trying to connect to that connection. But while I was connected, I did a quick ifconfig in case it would be helpful:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          inet6 addr: fe80::217:31ff:fea3:d83c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:976 errors:0 dropped:9 overruns:0 frame:0
          TX packets:1197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:988570 (965.4 KB)  TX bytes:195068 (190.4 KB)
          Interrupt:3 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          inet addr:169.254.5.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

eth1:avah Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          inet addr:169.254.6.239  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67843 (66.2 KB)  TX bytes:67843 (66.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:118.167.195.169  P-t-P:125.225.96.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:962881 (940.3 KB)  TX bytes:162592 (158.7 KB)


~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          inet6 addr: fe80::217:31ff:fea3:d83c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1184 errors:0 dropped:9 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1119573 (1.0 MB)  TX bytes:227592 (222.2 KB)
          Interrupt:3 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:24:58:67  
          inet addr:169.254.5.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

eth1:avah Link encap:Ethernet  HWaddr 00:17:31:A3:D8:3C  
          inet addr:169.254.6.239  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107485 (104.9 KB)  TX bytes:107485 (104.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:118.167.192.45  P-t-P:125.225.96.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:49830 (48.6 KB)  TX bytes:4310 (4.2 KB)

```

Thanks for any help. I really hope that I can use Ubuntu instead of Windows...if only I could get my Internet working. Thanks!

---

### Post by SpaceTeddy on 2008-04-19
as far as i am concerned, this is a misconfiguration given out by the ISP's. It sucks. But there is nothing to about it... ok, having that off my chest, here is a (possible ?) way to fix this. This came to mind thinking about the problem. I hope i am right and this is really worth a try...

The problem is that, unlike in windows, network manager always "assumes" a full ip connection. Since your router does not give out a lease, this does not happen, and ubuntu thinks the connection failed, while windows just stays connected and says "no connectivity" (which means there is a physical connection, but no configuration for it).

there are two (possible ?) ways i can think of how to avoid network manager shutting the link off again. One is to configure the network connection manually through the command line, the other is that you give yourself a static ip - ANY would do.

The second configuration would render your wireless useless in any other situation when you are trying to connect to an AccessPoint. So i will stick with the first one... just to see if it works. If it does, we can take it from there and automate it :)

the first thing you have to do it turn network manager off ! yes, off ! right-click on the symbol and uncheck "aktivate network".

once that i done, open up a console and type in the following (possibly changed) line to associate your network card with your access point :```
sudo iwconfig eth1 essid GW-AP11X
```
now, depending on your network security (encryption) this line might need some extra options. The example up there is ONLY for unencrypted networks. If you need a hint on how to do the encryption part, i'd need to know what kind of encryption is used. Also, the eth1 is **assumed** to be your wireless card. If it is not, change this to eth0 !

now, issuing the command
```
iwconfig
``` should show you something like this:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  **ESSID:"GW-AP11X" ** 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:31:AC:65:43:F2   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=84/100  Signal level=-48 dBm  Noise level=-49 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:338   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


the first bold line show what network you are connected to, the second shows the quality of your link.

Now, try to run ```
sudo pppoeconf
``` again and see if it pics up a modem. After that (if you not choose activiate the connection directly) use ```
pon dsl-provider
``` to activate the internet.

Hope it works :)

As a sidenode: The problem is that network-manager prohibits to stay connected to an access point if no ip configuration is received. This is potentially a bug in your case... maybe :) not sure about it.

---

### Post by ilych on 2008-04-19
SpaceTeddy, that worked **PERFECTLY**. Thank you so much!

This is very interesting.. I will have to do some reading to learn about ifconfig, iwconfig...and see what all these values mean. =]

Again, **thank you** for your prompt and accurate reply! Now I have another reason to not use my dual boot. Hehe. :)

---

### Post by chili555 on 2008-04-19
> I will have to do some reading to learn about ifconfig, iwconfig...and see what all these values mean. =]Linux has thoughtfully provided some great reading. Open a terminal and do:```
man iwconfig
man ifconfig
man <just about any command you want>
man woman
```You will be able to read about the meaning and usage of just about any command you want.

---

### Post by SpaceTeddy on 2008-04-20
ok, since that worked for you, i would like to point out that you are sending your dial in data of your ISP UNENCRYPTED over the air. This means, anybody near your house (about 50m -100m) with ANY mobile device can possibly sniff your login and use it. 
This either means they use it somewhere else, or just sniff it and then use YOUR connection to use the internet. I don't know if you care about that - but i would. 

just thought i point out that you are screaming your internet username and password to the world.

and i am glad i could help you :)

---

