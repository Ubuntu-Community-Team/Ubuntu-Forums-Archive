---
title: "Internet/ Network Problems - New 9.10 Install"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by plebeian on 2009-11-01
Hi Everyone,
I'm a Linux and Ubuntu newbie and installed KK with the Windows Installer. Everything went fine, easier than the W7 upgrade I did a few days previous. However there's been a weird problem with networking/ internet. At first the internet sort-of worked - some sites (anything Google and a few others) would work fine, some wouldn't at all, and some would load the title and hang (I have only tried in Firefox, as I think apt-get is affected by the problem as well, the software centre won't work). Anyway I tried fiddling around with the network settings and ended up just making it worse, and now the network is only working intermittently. I have tried clicking on the Network Manager button and selecting 'Auto Ethernet', this works sometimes but not always.

My net connection is done by an outside contractor with my university, through an ethernet port. I'm confident the hardware is working OK as it works fine in Windows.

I've trawled through this site and various documentation. If the answer is out there I've not found it, but not through lack of trying!

Any help greatly appreciated.

--Will

---

### Post by plebeian on 2009-11-04
I hope this isn't too soon to bump this thread; if it is, I apologise.

Anyway I have re-installed Ubuntu and now the network is back to where it was at the start. I'm not behind a proxy or firewall. I have tried using the OpenDNS servers, this just prevents anything from loading. I think my DNS is working OK as well, as I can ping sites OK, just not view them. I was able to download Chrome, it has the same problems as Firefox.

I'm pretty sure the DHCP is working, I have an IP address OK. However when I go to whatsmyip.org or similar sites I get given a different IP, which I assume is the IP of the location between the network and the internet.

I hope all of that made sense. I would really appreciate some help on this as I really want to start using Ubuntu properly, and until I can get connected and start adding some programs I can't do that.

Many thanks.
--Will

---

### Post by linux6994 on 2009-11-04
In a terminal window can you post your ifconfig?

Mine looks like this:
Using eth0 for charing.

eth0      Link encap:Ethernet  HWaddr 00:0d:60:7e:dc:79  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe7e:dc79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3247972 (3.2 MB)  TX bytes:11704 (11.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16201 (16.2 KB)  TX bytes:16201 (16.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:34:36:2f  
          inet addr:10.0.10.75  Bcast:10.0.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe34:362f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81689052 (81.6 MB)  TX bytes:10283060 (10.2 MB)

---

### Post by FiremanEd on 2009-11-04
You may want to have a look at this issue here.  [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757")

---

### Post by cariboo on 2009-11-04
Can you compare connection information between Windows 7 and Ubuntu. 

In Windows open a console and type:

```
ipconfig /all
```

In Ubuntu right-click the connection icon in the upper panel and select Connection Information, the results for the two should be the same.

---

### Post by plebeian on 2009-11-05
I've tried switching off the IPv6 in Firefox, like the bug report sggested, but that didn't help.

ifconfig results:
```
eth0      Link encap:Ethernet  HWaddr 00:23:54:0f:ff:cb  
          inet addr:10.1.1.160  Bcast:10.1.63.255 Mask:255.255.192.0
          inet6 addr: fe80::223:54ff:fe0f:ffcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1641 errors:87 dropped:0 overruns:0 frame:87
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1141330 (1.1 MB)  TX bytes:216214 (216.2 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:1f:f4:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-1F-F4-AA-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
ipconfig /all results:

```
Windows IP Configuration

   Host Name . . . . . . . . . . . . : Will-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : customer.ubs.vic.lan

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros AR928X Wireless Network Adapter
   Physical Address. . . . . . . . . : 00-22-43-1F-F4-AA
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : customer.ubs.vic.lan
   Description . . . . . . . . . . . : SiS Ethernet Controller
   Physical Address. . . . . . . . . : 00-23-54-0F-FF-CB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::702a:f564:48dd:3037%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.1.1.160(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.192.0
   Lease Obtained. . . . . . . . . . : 05 November 2009 11:21:48
   Lease Expires . . . . . . . . . . : 05 November 2009 11:36:48
   Default Gateway . . . . . . . . . : 10.1.0.1
   DHCP Server . . . . . . . . . . . : 10.1.0.1
   DHCPv6 IAID . . . . . . . . . . . : 167781204
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-10-63-E7-CB-00-23-54-0F-FF-CB

   DNS Servers . . . . . . . . . . . : 10.1.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{E22972A0-3702-4AEE-928D-81E31F682F57}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:10d5:2b5a:aee8:c7ea(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::10d5:2b5a:aee8:c7ea%14(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.customer.ubs.vic.lan:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : customer.ubs.vic.lan
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
```

Thanks guys
--Will

---

