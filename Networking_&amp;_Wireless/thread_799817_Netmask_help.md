---
title: "Netmask help"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by mirko_3 on 2008-05-19
Hello,
please clarify something for me. On my university network, I can get a dhcp lease without a hitch:
```

rumandfruit@sperelli:~$ sudo dhclient eth1  -d
There is already a pid file /var/run/dhclient.pid with pid 10898
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

rtap0: unknown hardware address type 803
rtap0: unknown hardware address type 803
Listening on LPF/eth1/00:0e:35:f4:80:80
Sending on   LPF/eth1/00:0e:35:f4:80:80
Sending on   Socket/fallback
DHCPREQUEST of 10.6.74.113 on eth1 to 255.255.255.255 port 67
DHCPACK of 10.6.74.113 from 1.1.1.1
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
SIOCADDRT: No such process
bound to 10.6.74.113 -- renewal in 121991 seconds.

```

Without a hitch, that is, I get an ip address; netmask however is automatically set to 255.255.255.0
This is the problem: for internet to actually work, I have to manually set the netmask to 255.255.0.0 and then reset the gw to 10.6.127.254. 
In other words, the default settings that dhclient wants to use - netmask 255.255.255.0 and gw 10.6.127.254 - do not work:
```

ping: unknown host google.com
rumandfruit@sperelli:~$ ping google.com

```

The funny thing is, I checked the computer of a friend of mine, with Windows on it; ipconfig shows me that they too have netmask 255.255.255.0, but it works.
Anyone?
Thank you

---

### Post by mirko_3 on 2008-05-20
Anyone?
It is my understanding (apparently wrong though) that if I'm on ip 192.168.1.* and on netmask 255.255.255.0, I can only communicate with other 192.168.1.* and not with say 192.168.0.*... but apparently this is not true? (see my friends' connection using windows)

---

### Post by mapes12 on 2008-05-20
The internationally-established private IP address ranges that can be assigned to internal network computers are as follows:

        * 10.0.0.1 through 10.255.255.254
              o 16,777,214 addresses
              o 16,777,214 computers on 1 network
                (10.x.x.x)
              o Uses a subnet mask of 255.0.0.0
              o First octet must be the same on all computers
              o A Class A address range 

        * 172.16.0.1 through 172.31.255.254
              o 1,048,574 addresses
              o 65,534 computers on each of 16 possible networks
                (172.16.x.x to 172.31.x.x)
              o Uses a subnet mask of 255.255.0.0
              o First two octets must be the same on all computers
              o A Class B address range 

        * 192.168.0.1 through 192.168.255.254
              o 65,534 addresses
              o 254 computers on each of 256 possible networks
                (192.168.0 to 255.x)
              o Uses a subnet mask of 255.255.255.0
              o First three octets must be the same on all computers
              o A Class C address range 

I would suggest speaking to your campus IT Manager to establish why DHCP is assigning a class C subnet mask to a class A IP range.

EDIT: Difficult to comment further about your friends XP client without having a look at the ```
ipconfig
``` output. Likewise, your ```
ifconfig
``` output would be interesting to see.

---

### Post by mirko_3 on 2008-05-21
Ok so there IS something non-standard here; I'm not going to chat with the IT managers, as I doubt they'd change the whole system just for one sole linux user :)

Here is my ifconfig output, on a windows computer it's just about the same.
```

eth1      Link encap:Ethernet  HWaddr 00:0e:35:f4:80:80  
          inet addr:10.6.74.113  Bcast:10.6.127.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1610987 (1.5 MB)  TX bytes:232891 (227.4 KB)
          Interrupt:21 Base address:0x2000 Memory:c8400000-c8400fff 

```

However I get an empty routing table - as mentioned, I have to manually change the netmask so as to be able to set the default gw (10.6.127.254):
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.6.74.0       0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

While on windows computers this evidently doesn't happen, I guess they are allowed to set 10.6.127.254 as default gw even with a 255.255.255.0 netmask...

---

### Post by YokoUno on 2008-05-21
[QUOTE=mapes12]I would suggest speaking to your campus IT Manager to establish why DHCP is assigning a class C subnet mask to a class A IP range.[/QUOTE]
Why not? The whole campus could be in 10.x.x.x with subnets here and there, each of them defined with appropriate masks. This is just a matter of design and possibility to use low-cost routers locally.

mirko_3, please post your /etc/network/interfaces

---

### Post by mirko_3 on 2008-05-21
```

rumandfruit@sperelli:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp

auto eth0

```

Here you go; I didn't know about this conf file, reading up its man page now. How does it work with NetworkManager?
BTW I'm connecting through wireless interface eth1; eth1, ath* and wlan* do not exist.

---

### Post by YokoUno on 2008-05-21
> How does it work with NetworkManager?
Badly, that's the least to say. It might be the cause of the quirk you noticed. This file is the native way to configure interfaces in debian, in a read-only use. But Network Manager **modifies this file** in some of its modes. I'd advise to stay out of its "roaming mode" if possible.

You should know that Network Manager can be uninstalled completely. It is safe to do so with sufficient experience of networking in debian. However, it's sometimes not trivial when wireless or usb devices are involved. But robust as soon as it's achieved :)

Anyway, references to eth2, ath0 and wlan0 can be safely deleted from your file, via sudo.
In addition, you should set eth1 as:
```

auto eth1
iface eth1 inet dhcp

```
then, when these modifications are saved:
```

sudo /etc/init.d/networking restart

```
which should initiate a request for a new lease for eth1 pronto.

---

### Post by mirko_3 on 2008-05-21
I checked things out, noticed how NetworkManager recognizes that I manually edited that file and turns its systray icon to "Manual Configuration"; however I doubt NetworkManager is the cause of it. I DO get the lease just as windows computers do - only it doesn't seem to be a valid configuration for linux. By deactivating NetworkManager (not uninstalling - a simlpe right-click-->deactivate) and manually running iwconfig and dhclient, I get the same results.
Anyhow thank you for your help, and I *will* try uninstalling NetworkManager (though I find it very convenient for laptops) and see, just not now as I'm working on an assignment. I will report back in a few days, I just don't want to break something now and have to spend an hour fixing it.

---

### Post by YokoUno on 2008-05-21
> just not now as I'm working on an assignment
Perfectly valid, but FYI network-manager and avahi-autoipd are just packages which can be safely removed and reinstalled if anything goes wrong.

It's a matter of seconds, thanks to the debian apt system ;)

---

### Post by mapes12 on 2008-05-21
Please accept my apologise if I have mentioned this before. It's been a long day. An excellent replacement for Network Manager is 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It has a Ubuntu package to install it.

Having looked at the subnetmasks allocated on your private IP address range for your campus I'm amazed how windoze clients are interpreting none standard IP addresses..................or is it all a big conspiracy where nothing works but nobody dare say anything (joke).

But seriously, I would contact your IT Manager and ask the question. The rest of us would be very interested in the response please? Show him/her my previous thread with regard to private IP address ranges for comment :lolflag:

---

### Post by The Cog on 2008-05-21
Windows will broadcast an ARP request for the default gateway's address regardless of whether the netmask indicates it is on the same network or not. I just proved that with wireshark. 

Linux (and most networking kit I know of) will not accept a default gateway address that is not on the local network - it just doesn't make sense. 

I believe the DHCP server is misconfigured. I see two possible errors:
1) The announced netmask is wrong, or 
2) The announced default gateway is wrong but the local router is running proxy-arp to help misconfigured hosts.

---

### Post by mirko_3 on 2008-05-22
Very well, I'll try asking and give wicd a run Monday, thanks for the support. I'll report back.

---

