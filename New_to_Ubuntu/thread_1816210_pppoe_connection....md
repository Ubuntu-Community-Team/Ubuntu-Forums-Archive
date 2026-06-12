---
title: "pppoe connection..."
date: 2011-08-01
forum: New to Ubuntu
---

### Post by C R Sharma on 2011-08-01
Hi friends...!!!

With the help of u people I got rid of few of my previous problems. Thanks for that. But again I m in the middle of some problem. The problem is related with internet connection using dsl-modem. As I m using dual boot(win-7 & ubu-11.04), it is okay with win-7. after the dsl got stablized i boot-up my pc & go ahead with internet connection in win-7 but the problem lies with ubuntu. with the help of many queries & their answers, I tried to solve the problem myself, but all in vain. This is the situation.

1. checked for pppoe installation using "dpkg -s pppoeconf" and it is okay.
2. using network manager, created dsl setup , but even no response of connection name.
3. "sudo pppoeconf" finds the device as "eth0", but while scanning it says "not connected" (dsl status is alright on modem). Respond as "... access concentrator of yr provider did not respond. check for connection or other reason of another running pppoe process...." (.)

kindly help to resolve this. Keep in mind that I m only a learner/ beginner (.)

thanks..!!!

---

### Post by lkraemer on 2011-08-01
I assume you are using an Ethernet Patch cable from the DSL Modem to Wonders.  Since the Wonders machine can access the Internet you must
have the proper Login & Password associated with your DSL Provider.

So, boot Ubuntu and plug that same Etherent Patch Cable into the Ubuntu
machine.  Then open a Terminal Window (Console) and type these commands:
```

sudo ifconfig
sudo iwconfig

```
to see what is displayed.

Next I'd try:
```


ping www.yahoo.com -c3
ping 209.191.122.70 -c3

```
If you get good pings to Yahoo, then you are connected.  If you can't
ping yahoo then check that you have DNS Servers assigned.  I use the 
OpenDNS Servers.

I also assume you know the Router ESSID, and have found the proper
Ethernet connection name with the above commands.  eth0 eth1 etc.


**Manual Choice:**
If you know the routers essid and the correct <interface=eth0>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
below:
```

sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo iwconfig eth0 essid "ThomsonE3A467"
sudo iwconfig eth0 mode Managed
sudo ifconfig etho up
sudo dhclient eth0
iwconfig

```
Then try:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```

Post the output of what doesn't work.

lk

---

### Post by dineshs on 2011-08-03
Are you sure your DSL modem is in *bridge mode*?Can you post the result of ```
ipconfig /all
```when the connection is working fine on win7?

---

### Post by Wim Sturkenboom on 2011-08-03
> **C R Sharma said:**
>  "not connected" (dsl status is alright on modem). Respond as "... access concentrator of yr provider did not respond. check for connection or other reason of **another running pppoe process**...." (.)
If the (attempted) configuration is still in the networkmanager, remove it from there.

It might do the trick.

---

### Post by C R Sharma on 2011-08-04
Kindly refer to <ikraemer> reply

Following are the results;

<sudo ifconfog>
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:db:29:9f  
          inet6 addr: fe80::baac:6fff:fedb:299f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78 (78.0 B)  TX bytes:3416 (3.4 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

<sudo iwconfig>
lo        no wireless extensions.

eth0      no wireless extensions.

<ping [www.yahoo.com](www.yahoo.com) -c3>
ping: unknown host [www.yahoo.com](www.yahoo.com)

<ping 209.191.122.70 -c3>
connect: Network is unreachable

 I could not understand eesid:(

other results are as


<route>
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         MyDslModem.loca 0.0.0.0         UG    0      0        0 eth0

<route -n>
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

<route -nee>
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface    MSS   Window irtt
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0     0     0      0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0     0     0      0

<netstat -r>
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         MyDslModem.loca 0.0.0.0         UG        0 0          0 eth0

<ping 192.168.1.1>
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=128 time=0.395 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=128 time=0.373 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=128 time=0.368 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=128 time=0.377 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=128 time=0.374 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=128 time=0.369 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=128 time=0.376 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=128 time=0.371 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=128 time=0.384 ms

64 bytes from 192.168.1.1: icmp_req=10 ttl=128 time=0.382 ms
64 bytes from 192.168.1.1: icmp_req=11 ttl=128 time=0.380 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=128 time=0.380 ms
^C
--- 192.168.1.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 10997ms
rtt min/avg/max/md


Kindly suggest in this regards....//

---

### Post by lkraemer on 2011-08-05
OK, you need to take one step backwards.  Usually the Etherent to
DSL Modem is Plug & Play, but in your case you attempted to configure
it with pppoeconf.  Here is some information that should help.
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

I'd doublecheck your files:
chap-secrets
Peer file

Also as dineshs suggested .....in Windows post the output of:
```

ipconfig /all

```

REF:
[http://sharannetwork.blogspot.com/2011/02/what-is-pppoe-and-bridge-mode-of-adsl.html](http://sharannetwork.blogspot.com/2011/02/what-is-pppoe-and-bridge-mode-of-adsl.html)


lk

---

### Post by C R Sharma on 2011-08-05
Following are the results;
 
<ipconfig /all>
No command 'ipconfig' found, did you mean:
Command 'tpconfig' from package 'tpconfig' (universe)
Command 'iwconfig' from package 'wireless-tools' (main)
Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found
 
<dpkg -s pppoeconf>
Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 340
Maintainer: Ubuntu Developers <[EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]>
Architecture: all
Version: 1.19ubuntu1
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Original-Maintainer: Gregory Colpart <[EMAIL="reg@debian.org"]reg@debian.org[/EMAIL]>
<sudo pppoeconf>
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; ALL DEVICES FOUND? &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474; 
&#9474; I found 1 ethernet device: &#9474; 
&#9474; eth0 &#9474; 
&#9474; &#9474; 
&#9474; Are all your ethernet interfaces listed above? &#9474; 
&#9474; (If No, modconf will be started so you can load the card &#9474; 
&#9474; drivers manually). &#9474; 
&#9474; &#9474; 
&#9474; Or press ESC to abort here. &#9474; 
&#9474; &#9474; 
&#9474; &#9474; 
&#9474; <Yes> <No> &#9474; 
&#9474; &#9474; 
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
 
after scaning it says:
 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; NOT CONNECTED &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474; 
&#9474; Sorry, I scanned 1 interface, but the Access &#9474; 
&#9474; Concentrator of your provider did not respond. Please &#9474; 
&#9474; check your network and modem cables. Another reason for &#9474; 
&#9474; the scan failure may also be another running pppoe &#9474; 
&#9474; process which controls the modem. &#9474; 
&#9474; &#9474; 
&#9474; &#9474; 
&#9474; &#9474; 
&#9474; &#9474; 
&#9474; &#9474; 
&#9474; <Ok> &#9474; 
&#9474; &#9474; 
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by dineshs on 2011-08-06
> <ipconfig /all>
No command 'ipconfig' found, did you mean:
Try the command in windows *not* ubuntu

---

### Post by C R Sharma on 2011-08-06
<ipconfig /all>
Windows IP Configuration
   Host Name . . . . . . . . . . . . : CRSharma-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : local.lan
Ethernet adapter Local Area Connection:
   Connection-specific DNS Suffix  . : local.lan
   Description . . . . . . . . . . . : Realtek RTL8168D/8111D Family PCI-E Gigab
it Ethernet NIC (NDIS 6.20)
   Physical Address. . . . . . . . . : B8-AC-6F-DB-29-9F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::2003:3a8d:9a12:f698%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.3(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, August 06, 2011 3:32:43 PM
   Lease Expires . . . . . . . . . . : Sunday, August 07, 2011 6:35:23 AM
   Default Gateway . . . . . . . . . : fe80::225:5eff:fe92:79e8%11
                                       192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Tunnel adapter isatap.local.lan:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : local.lan
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter 6TO4 Adapter:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Teredo Tunneling Pseudo-Interface:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:3481:3fe4:3f57:fefc(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::3481:3fe4:3f57:fefc%13(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
Tunnel adapter Reusable Microsoft 6To4 Adapter:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 9:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 11:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 12:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #5
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 13:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 14:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #7
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

### Post by C R Sharma on 2011-08-11
HI dineshs &  lkraemer and others too..//
 
not recvd any suggetions from u agn..!!
 
anything u want 2 know for further troubleshoot my problem..//
 
there r lot others to come ...but i want 2 solve this first..??
 
thanks:(

---

### Post by dineshs on 2011-08-11
Please post the results of ```
sudo lshw -C network
```
```
sudo dhclient eth0
```and
```
ping 4.2.2.1 -c3
```
Do you use a dialler in windows?

---

