---
title: "[SOLVED] new notebook, no wired connection through linksys hub"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by jeffsa12 on 2008-11-29
I got my new Acer Aspire 5520-5908 a few days ago. I set it up to dual boot Vista / Ubuntu 8.10 64amd. Nice notebook for $399 newegg.

I have everything in Ubuntu working great except the ability to connect to my wired home network (using DHCP). I can get net access by connecting directly to my DSL modem, but not through my Linksys NH1005 5 port hub.

I have 2 desktops with various multi boot and virtual OS's, that have always connected to my network....

I have tried swapping cables, ports, OS's (Vista and Ubuntu) and the same results.....will connect to internet by bypassing my network hub, but will not connect through it.
 
NVidia MCP67 ethernet....I'll connect with the notebook if anyone wants more hardware details or my ifconfig output.

---

### Post by cmnorton on 2008-11-29
Basically, this sounds like you need to put the DSL modem into "pass-thru" mode, but I am not sure how to do that with a hub. For that matter, I am not sure how to re-setup my Linksys router and DSL modem. It's been years since I set it up.

Look at this link for your hub. A similar question is being asked:
[http://forums.linksys.com/linksys/board/message?board.id=Hubs&message.id=35](http://forums.linksys.com/linksys/board/message?board.id=Hubs&message.id=35)

---

### Post by jeffsa12 on 2008-11-30
Ok...
I believe my ADSL modem (Actiontek GT701) is also a router. I configure it through a web browser, going to the addy 192.168.0.1

It's set up to assign DHCP as follows:

 DHCP Settings

Your High Speed Internet DSL Modem will automatically assign an IP Address to each device in 
your network. If you are using an additional Router to assign these IP Addresses, you will 
need to turn this function Off.

Please make your selection and then click Apply to save your changes.

DHCP Server
 On X    Off
 I would like to adjust the DHCP Server settings.   

Once you have adjusted your settings below, please click Apply to save your changes.


Beginning IP Address: 	192.168.0.2
Ending IP Address: 	192.168.0.255
Subnet Mask: 	        255.255.255.255

DNS: X  Dynamic   Static  
DNS Server 1: 	
DNS Server 2: 	

When I connect my notebook directly to the modem to get a connection, it gets assigned ip 192.168.0.3.

Why this ip and not xxx.xxx.x.4 ? Could the router keep track of the lan card hardware # HWaddr 00:1b:38:d1:a3:c2  and associate it with the 192.168.0.3 ip?
Causing problems if my desktop is already hooked up through the hub and also being assigned 192.168.0.3 ???



```
jeff@jeff-laptop:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
lo        16436 0        14      0      0 0            14      0      0      0 LRU

```

```
root@jeff-laptop:/home/jeff# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:d1:a3:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:904 (904.0 B)  TX bytes:904 (904.0 B)
```

```
root@jeff-laptop:/home/jeff# dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:38:d1:a3:c2
Sending on   LPF/eth0/00:1b:38:d1:a3:c2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by cmnorton on 2008-11-30
It may be that you have to reboot everything, although your dhcp should have known .3 was assigned. Was it statically assigned previously, and you need to set the desktop to dhcp?

Did you click on something in the router config that is assigning an address based on mac address. I've never heard of a router giving the same address. That is wierd.

---

### Post by jeffsa12 on 2008-11-30
Hey thanks for your input cmnorton!

> Was it statically assigned previously, and you need to set the desktop to dhcp?

No, I just plugged them in and everything worked. My desktops (2) have been hooked up for a long time before I got the notebook. The router assigned them ip 192.168.0.2 for (old computer) and 192.168.0.3 for (new computer).
As I said previously, I currently have a multiboot setup on (new) with 2 windows OS's and 3 linux OS's. I also have Vbox and VMware workstation with a win95 setup, Callyway OSX, BSD, and several linux distro's that rotate in and out.....I have got most of the "normal" OS's connected to the network, no luck with win95 and osx, but not worried about them....

> Did you click on something in the router config that is assigning an address based on mac address.

No, I didn't... and looking into the setup, I don't see an option for that.

> I've never heard of a router giving the same address. That is wierd. 
Yea...that doesn't seem right to me either....
**Anyone have some info regarding this issue?? **

> It may be that you have to reboot everything
Yea I have tried that several times already.

---

### Post by jeffsa12 on 2008-11-30
More....

I got DHCP to reassign all the ip address's. 

(new desktop) 192.168.0.2
(old desktop) 192.168.0.4
(notebook)    0.0.0.0 through hub, no connection

this was after many attempts to get a connection through the hub.
(notebook)    192.168.0.2 bypassing hub

I read somewhere late last night while nodding off,

......if you use Linux drivers for some lan cards (hardware), for the first, initial network connection, rather than windows drivers, that this would create problems in that hardware thereafter......

That is if I understood what I read correctly. I don't recall further details and do remember that the info was quite dated.

It seems that this must be a hardware issue as neither Linux or Windows will connect through the hub, but both will connect directly, bypassing the hub!?!?

Is there a way to "refresh all settings" in the hardware, on board lan?

I recall fighting with windows years ago with driver issues for pci card hardware, and resorted to physically removing and reinstalling the card to get a problem resolved.

---

### Post by jeffsa12 on 2008-12-10
A new Rosewill RC-405 10/100Mbps SOHO switch ( $15.00 )to replace my Linksys hub solved the problem.

The lan hardware in my notebook was incompatible with my Linksys hub.

---

### Post by jeffsa12 on 2008-12-10
Also got my new notebook's wireless (Atheros AR242x) working today in Ubuntu 8.10 amd64 by adding an EDIMAX EW-7206APG Wireless access point to my Rosewill RC-405 10/100Mbps SOHO switch.

This new network hardware is pretty much plug and play....except securing the wireless. For hardware details see: [http://ubuntuforums.org/showthread.php?t=999462](http://ubuntuforums.org/showthread.php?t=999462)

For Atheros wireless, I followed the post by reasoner at : [http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860) .

---

