---
title: "Wireless Not Working"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by kyle99 on 2008-10-16
Ok, so I'm using 8.10 beta, and I plug in my netgear wg111v3 and it works and recognizes it, and it shows a list of networks available. I choose my network and enter the password, and it succesfully connects and says it's signal strength is like 44%. But all my pages in firefox don't load due to a page load error. How do I fix this?

---

### Post by superprash2003 on 2008-10-16
post output of ifconfig and iwconfig

---

### Post by kyle99 on 2008-10-16
> kyle@kyle-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:93:5a:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:203732 (203.7 KB)  TX bytes:203732 (203.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:c7:f2:4d  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fec7:f24d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2739 (2.7 KB)  TX bytes:8912 (8.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-C7-F2-4D-32-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kyle@kyle-desktop:~$ 













> kyle@kyle-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Thomas"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1E:2A:75:15:E0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=34/100  Signal level:-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kyle@kyle-desktop:~$ 


Thanks in advance!

~Kyle

---

### Post by superprash2003 on 2008-10-17
ok.. you are able to get an ip address(192.168.1.8).. so thats good.. now type in the following two commands and post output of it
1)ping 192.168.1.1
2)ping google.com

---

### Post by kyle99 on 2008-10-17
First one:

```
kyle@kyle-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

```

Google:

```
From 192.168.1.8 icmp_seq=15 Destination Host Unreachable
From 192.168.1.8 icmp_seq=16 Destination Host Unreachable
From 192.168.1.8 icmp_seq=17 Destination Host Unreachable
From 192.168.1.8 icmp_seq=19 Destination Host Unreachable
From 192.168.1.8 icmp_seq=20 Destination Host Unreachable
From 192.168.1.8 icmp_seq=21 Destination Host Unreachable
From 192.168.1.8 icmp_seq=23 Destination Host Unreachable
From 192.168.1.8 icmp_seq=24 Destination Host Unreachable
From 192.168.1.8 icmp_seq=25 Destination Host Unreachable
From 192.168.1.8 icmp_seq=27 Destination Host Unreachable
From 192.168.1.8 icmp_seq=28 Destination Host Unreachable
From 192.168.1.8 icmp_seq=29 Destination Host Unreachable
From 192.168.1.8 icmp_seq=31 Destination Host Unreachable
From 192.168.1.8 icmp_seq=32 Destination Host Unreachable
From 192.168.1.8 icmp_seq=33 Destination Host Unreachable
From 192.168.1.8 icmp_seq=35 Destination Host Unreachable
From 192.168.1.8 icmp_seq=36 Destination Host Unreachable
From 192.168.1.8 icmp_seq=37 Destination Host Unreachable
From 192.168.1.8 icmp_seq=39 Destination Host Unreachable
From 192.168.1.8 icmp_seq=40 Destination Host Unreachable
From 192.168.1.8 icmp_seq=41 Destination Host Unreachable
From 192.168.1.8 icmp_seq=43 Destination Host Unreachable
From 192.168.1.8 icmp_seq=44 Destination Host Unreachable
From 192.168.1.8 icmp_seq=45 Destination Host Unreachable
From 192.168.1.8 icmp_seq=47 Destination Host Unreachable
From 192.168.1.8 icmp_seq=48 Destination Host Unreachable
From 192.168.1.8 icmp_seq=49 Destination Host Unreachable
From 192.168.1.8 icmp_seq=51 Destination Host Unreachable
From 192.168.1.8 icmp_seq=52 Destination Host Unreachable
From 192.168.1.8 icmp_seq=53 Destination Host Unreachable
From 192.168.1.8 icmp_seq=55 Destination Host Unreachable
From 192.168.1.8 icmp_seq=56 Destination Host Unreachable
From 192.168.1.8 icmp_seq=57 Destination Host Unreachable
From 192.168.1.8 icmp_seq=59 Destination Host Unreachable
From 192.168.1.8 icmp_seq=60 Destination Host Unreachable
From 192.168.1.8 icmp_seq=61 Destination Host Unreachable
From 192.168.1.8 icmp_seq=63 Destination Host Unreachable
From 192.168.1.8 icmp_seq=64 Destination Host Unreachable
From 192.168.1.8 icmp_seq=65 Destination Host Unreachable

And it keeps doing stuff like that.

```

---

### Post by superprash2003 on 2008-10-18
hey did you manually enter ip address as 192.168.1.8 ?? or did you get it automatically via DHCP from your router?

---

### Post by kyle99 on 2008-10-18
Automatically via DHCP.

---

### Post by superprash2003 on 2008-10-19
ok this is starting to get a bit strange.. your router gives you an ip 192.168.1.8 . but pinging 192.168.1.1 doesnt give any reply??? do you have firestarter or anything similar running??

---

### Post by Bucky Ball on 2008-10-19
In Firefox:

**Edit->Preferences->Network->Settings**

and make sure 
[B]
Auto detect proxy settings for this network[/B]

is marked. Might be the problem ...

---

### Post by MrWES on 2008-10-19
Try powering down the router and bring it back up. Maybe it's not picking up the MAC address on that card.

---

### Post by kyle99 on 2008-10-19
> **superprash2003 said:**
> ok this is starting to get a bit strange.. your router gives you an ip 192.168.1.8 . but pinging 192.168.1.1 doesnt give any reply??? do you have firestarter or anything similar running??
No, nothing like that. It's a fresh installation.

---

### Post by kyle99 on 2008-10-21
Anyone? Anyone? Bueler...

---

### Post by onfyreforjesus on 2008-10-29
I'm having the exact same problem. No it is not a router issue cos i have dual boot and the thing works perfectly on windows.

amy help. since this is the v3 adapter with ndiswrapper things are worse-- It doesn't even connect to my home network. Thats protected with a WEP Key.

Any help?

---

### Post by sideshowmel on 2008-10-30
Same problem here.

Multiple WLAN's with different SSID's, encryption methods, etc.

Worked fine when I first installed the Ibex rc, then I upgraded all packages and now it's broken. (I updated over ethernet, not wifi, and I've heard that can make a difference).  I tried removing some routes to no avail.

BTW it's not a router / MAC address / NIC card problem... I can connect fine to all wireless networks in Windoze, and WIRED ethernet in Ibex and Windoze works fine, too.


EDIT EDIT EDIT

All I had to do was add the following line to /etc/shorewall/interfaces file:
net     wlan0          detect	      	      tcpflags

I feel really stupid today...

---

### Post by onfyreforjesus on 2008-10-31
ANything yet? I managed to get it work with the native rtl8187 module but i was just 1 metre away from the router, albeit at only 50% of the usual speed. I have tried wpa wep everything anyone got this thing to work with ndiswrapper?

---

### Post by onfyreforjesus on 2008-10-31
Alright, I finally managed to get this to work.  You can follow the various howto's and install the driver using ndiswrapper. 

I'm running the final release with all updates as of today of the Intrepid Ibex: ubuntu 8.10

WEP security does not work.

You have to use WPA2 personal security. That is the option i have on my linksys wrt54G v5 router.

Also I have my MAC filter protection on.

Seems to work well as of now. Hope this helps. I'm just waiting for the opensource rtl8187b module to get ready. 

Thanks guys, hope this helps.

---

### Post by onfyreforjesus on 2008-10-31
Got it to work using WPA2 security and my MAC filtering is on.

Thanks and hope this helps.

---

