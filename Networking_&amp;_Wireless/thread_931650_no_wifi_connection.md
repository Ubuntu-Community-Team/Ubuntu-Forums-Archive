---
title: "no wifi connection"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by badgandalf on 2008-09-27
For some reason (I believe I had some automatic updates, but am not even sure), my wifi connection stopped working. I'm running Kubuntu Hardy and the thing is I can see the network SSID, but when I click on connect it stays there for a while and then reports that it couldn't connect. I've tried connecting from Windows and it works so the problem has to be somewhere here (in Ubuntu, I mean).

In case it helps, this is what I get out of ifconfig:

[I]eth0      Link encap:Ethernet  HWaddr 00:16:17:e9:12:04  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fee9:1204/64 Scope:Link            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1            
          RX packets:16506 errors:0 dropped:0 overruns:0 frame:0        
          TX packets:16313 errors:0 dropped:0 overruns:0 carrier:0      
          collisions:0 txqueuelen:1000
          RX bytes:10022770 (9.5 MB)  TX bytes:13375327 (12.7 MB)
          Interrupt:21 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12908 (12.6 KB)  TX bytes:12908 (12.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:88:a6:73:c7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xf800
[/I]

And this is the content of my interfaces file
[I]
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0[/I]

I've also tried adding some lines as suggested in some other posts, but it always comes back to this.

Have there been any problems with an update I'm not aware of or does anyone have any ideas as to how to resolve the issue? Thanks a lot,

Ignacio

---

### Post by badgandalf on 2008-09-28
Bump

---

### Post by superprash2003 on 2008-09-28
try connecting manually.  go to system->admin->network go to wlan0 properties and disable roaming mode..

---

### Post by badgandalf on 2008-09-28
Roaming mode? I cannot find such an option. Where is it? Ignacio

---

### Post by superprash2003 on 2008-09-29
go to system->admin->network.. there select "wireless connection" and click on properties.. on the top left of the window . uncheck "Enable Roaming Mode"

---

### Post by badgandalf on 2008-09-30
Mmmm.

Can't find it. I get to wireless properties and get options such as TCPIP, ESSID, and so forth but no 'roaming' option. I f I enable the TCPIP with dhcp, give the correct ESSID and WEP password it tries to connect but fails.

Ignacio

---

### Post by superprash2003 on 2008-09-30
in that page itself.. under tcp/ip instead of using DHCP. enter ip address manually and try..

---

### Post by badgandalf on 2008-09-30
No. I give it an IP address within my home network but it does not connect. Rgds,

ignacio

---

### Post by badgandalf on 2008-10-11
Ok, I made some progress. Now I can connect if I disable WEP encryption using WICD. Also, I saw that sometimes I get an error saying 'Could not parse the XML output from the network configuration backend' or something similar. Would that trigger new ideas to try?

Thnx
Ignacio

---

