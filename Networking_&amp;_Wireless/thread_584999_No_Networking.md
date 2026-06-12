---
title: "No Networking"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by gamx on 2007-10-21
I have upgraded from Feisty to Gutsy and I cannot connect to the internet. There seem to be many things going on (although probably related):
1. If I am trying to connect to a wired network through my router it does not work (it used to work with Feisty with the same setup). I can only connect if I plug the cable directly to the cable modem. Otherwise it says it cannot obtain an address.
2. If I try to connect wirelessly things are even worse. I have a linksys WPC11 card that I configure through ndiswrapper. With Feisty it was working great, here it does not work at all. First, checking for the signal it does not work (it always says that there is no signal) and not only when I do it with  NetworkManager.
Second, if I connect to an unprotected network it sort of works, but NetworkManager keeps on saying that the quality of the signal changes (from 1% to 90%). But here comes the worse part, if I a connect to a protected network and I write the password the whole computer freezes. It freezes completely and I need to use the button. Sometimes it also freezes even if I use and unprotected network.

Are these problems related? Is there any solution? I am kind of desperate about it. I would appreciate any ideas.

---

### Post by gamx on 2007-10-21
Here is more information. If I use ifconfig I get the following output

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:A0:9E:E0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84988 errors:0 dropped:0 overruns:1 frame:0
          TX packets:35412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88939485 (84.8 MB)  TX bytes:2847854 (2.7 MB)
          Interrupt:11 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:DB:A0:9E:E0  
          inet addr:169.254.10.122  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50084 (48.9 KB)  TX bytes:50084 (48.9 KB)

Why I have an eht0:avahi address and not eth0?

---

### Post by terra808 on 2007-10-21
same problem here ...wired..same results

---

### Post by paulstaf on 2007-10-21
I have had the same issues, Evolution times out trying to check my email, Pidgin won't connect to any of the IM providers, and Firefox couldn't find a web page at all.

For now, the fix seems to be to edit your /etc/resolve.conf file and manually add some DNS servers in there.

nameserver 208.67.222.222
nameserver 208.67.220.220

I read something in here about how DNS isn't working correctly via DHCP.  I had my DNS server set as my router address as it is supposed to forward, but it only worked marginally.

I only got real results when I put the above nameservers in there.

Good luck!

---

### Post by gamx on 2007-10-21
I have changed the DNS and things are not working either. However, I have narrowed down things a little.

1. If I start the computer with my PCMCIA wireless out card and I plug it in after boot up, Ubuntu detects it perfectly and everything works like. No freezes no lost signals and the like. Not perfect but it is better than nothing.
2. Regarding the wired connection I think that this must be a DHCP problem. When I try to connect manually I get the following error message:

 sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 27828
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:db:a0:9e:e0
Sending on   LPF/eth0/00:0b:db:a0:9e:e0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Even though a "lease" was offered by my router.

---

### Post by gamx on 2007-10-22
Good news. It seems that the wired problem was not ubuntu but the router. I do not know why but it  does not "lease" addresses... although it works properly when one tries to connect wirelessly...
The only outstanding problem is the wireless one now.

---

