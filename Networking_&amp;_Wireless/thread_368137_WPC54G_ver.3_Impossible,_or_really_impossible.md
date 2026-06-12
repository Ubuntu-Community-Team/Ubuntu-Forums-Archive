---
title: "WPC54G ver.3: Impossible, or really impossible?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by kameneye on 2007-02-22
*[SIZE="4"]Getting the WPC54G card to work is like the common cold; everyone has their own remedy, but even though you try everything, nothing works.[/SIZE]*

That's my philosophy on my card.  The Linksys WPC54G version 3.  I am just getting tired of the entire week of sitting down for hours on end trying to make it work. I have yet to come close to getting this thing to work. 

With ndiswrapper, I am using the drivers that came with the disk that came with the card, and *ndiswrapper -l* reads that both the driver and hardware are present, but I cannot make the card appear anywhere else due to the blacklisted bcm43xx driver.  Somewhere along those lines, with the "I need the bcm43xx driver to 'see' the card, but if its there, I cannot use the card" loop, is where I need the expert advice of you all to assist me.  If anyone sees that this is not the problem, do not hesitate to speak up.

I am running Edgy, which seems to be more troublesome with the card than Dapper is...

If any of you need results from commands, I would be more than happy to post them here.

Thanks to all who bothered (will bother) to help a poor n00b as myself.

---

### Post by jml on 2007-02-22
post the outputs of the following commands:

ifconfig

iwconfig

---

### Post by kameneye on 2007-02-23
Ifconfig:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:8A:36:CA:EA  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:fe36:caea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4327822 (4.1 MiB)  TX bytes:761461 (743.6 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

