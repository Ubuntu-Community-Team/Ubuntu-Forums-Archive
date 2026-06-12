---
title: "LAN connection on a campus network"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by matt18712 on 2007-03-02
I just built my own computer and after installing windows xp pro and having everything work fine, i decided to try out linux. Ubuntu was recommended by a friend so here i am.
Installation went smooth, but now trying to connect to my campus LAN is causing a headache. 
In windows my connection settings for HTTP are proxy.gcc.edu:8080
I've tried setting System->Preferences->Network Proxy to these settings, but no luck.
In windows my IP is given by a computer withing my building at 10.33.0.1

My computer:
ASUS P5N32-E SLI Plus 650i ATX || C2D E6300 Conroe 1.86GHz || CORSAIR XMS2 2GB (2x1GB) 800-6400 TWIN2X2048-6400 || ZALMAN CNPS9500 AT  || XFX PVT73GUGD3 GeForce 7600GT 256MB PCIE-x16
WD Caviar SE WD800JD 80GB 7200 SATA2 || SAMSUNG 18X DVD±R E-IDE/ATAPI Model SH-S182D
XION Supernova ATX 600W || LIAN LI PC-61 Black Aluminum ATX Mid-Tower

I should note that i had previously been successful at accessing the campus network with my laptop (tc1100 tablet) with build 6.06.1 while just messing around on the liveCD. So i know it should work :neutral: 

Any help/suggestions/links would be greatly appreciated. Thanks

---

### Post by finer recliner on 2007-03-02
my university has a very powerful firewall (called ResNet) in place.

it doesnt work so well with linux. i had to apply a patch to one of my config files to get my internet connection to work well

i suggest calling your CIT help desk or similar service and seeing if they have a work around available for linux users.

---

### Post by matt18712 on 2007-03-02
But it worked on my laptop from the liveCD about a month ago, so i don't think that'd be it. :-/

---

### Post by punx45 on 2007-03-03
assuming you went with autoconfigure/DHCP during the install..

in the terminal do 'ifconfig' and see if you are getting an IP address.. if you arent sure you can paste the output of that here.

try pinging things too, like IPs within the campus network and outside as well.   unlike in windows, the linux ping will keep going until you tell it to stop (CTRL-C) or specify a number of times with the command (i.e. 'ping -c 5 10.33.0.1') will ping your network gateway 5 times.

did you use the proxy settings with the live CD?   you might also want to try undoing the proxy setting as you did it, and applying it just in the web browser and see how that works for ya.

I applied to Grove City.. got waitlisted :-|

---

### Post by matt18712 on 2007-03-03
Ok, i tried ifconfig and it showed both of my ethernet ports with no IP from either. One of the connections shows a line "inet6 addr: (something that looks like a MAC addr) Scope:Link" So i imagine that's the one that's plugged in.
A ping to any IP address gave me "connect: Network is unreachable". 
I just tried using the DNS servers that windows cmd prompt spit back from "ipconfig -all" but that didn't help either. It's starting to get pretty frustrating.

---

### Post by bapoumba on 2007-03-03
Hello,
could you post the output to **cat /etc/network/interfaces** and **cat /etc/resolv.conf** ?

---

### Post by matt18712 on 2007-03-04
Ok, i decided to run the new Fiesty Herd 5 from my laptop to see if it worked with the internet. It does. All i had to do was set the proxy in Firefox and all is well. I'm posting from Fiesty right now. The output from ifconfig shows an IP was successfully pulled from the DHCP server of my building. So the campus is NOT the problem. 
So back to the desktop... I'll edit this post once i have ran the code requested. 
I have the feeling that the problem still lies in my ethernet controller (it listed itself as MCP55, some googling showed that to be nforce430? which apparently has problems with ubuntu). Most posts i've come across have an end result of buying some cheap-o network card for 10 dollars. But , i'm an engineer, i just want to solve the puzzle.
EDIT:

Output from Terminal using Fiesty Herd 5 LiveCD:
Code:

ubuntu@ubuntu:~$ ifconfig

eth0      
Link encap:Ethernet  HWaddr 00:1A:92:5B:95:7F            
inet6 addr: fe80::21a:92ff:fe5b:957f/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)          
Interrupt:16 Base address:0xe000 

eth1      
Link encap:Ethernet  HWaddr 00:1A:92:5B:A5:85            
UP BROADCAST MULTICAST  MTU:1500  Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)          
Interrupt:17 Base address:0xc000 

eth0:avah 
Link encap:Ethernet  HWaddr 00:1A:92:5B:95:7F            
inet addr:169.254.7.31  Bcast:169.254.255.255  Mask:255.255.0.0          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
Interrupt:16 Base address:0xe000 

eth1:avah 
Link encap:Ethernet  HWaddr 00:1A:92:5B:A5:85            
inet addr:169.254.7.125  Bcast:169.254.255.255  Mask:255.255.0.0          
UP BROADCAST MULTICAST  MTU:1500  Metric:1          
Interrupt:17 Base address:0xc000 

lo        
Link encap:Local Loopback            
inet addr:127.0.0.1  Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:186 errors:0 dropped:0 overruns:0 frame:0          
TX packets:186 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:0 
RX bytes:14068 (13.7 KiB)  TX bytes:14068 (13.7 KiB)

ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

From the full install of Edgy:
interfaces:
(everything as before, except with eth0, eth1, eth2, and wlan0) all set to dhcp as before)

resolv.conf spit back nothing. I typed it as is. It changes only when i change proxy settings with Network Proxy in System-Preferences. But that isn't what i need to do to get online. So it should be blank correct?


(another edit: If i disconnect the ethernet cable ubuntu locks up. I think that's significant. Let me know what else you need)

---

