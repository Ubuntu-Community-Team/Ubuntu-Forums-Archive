---
title: "[SOLVED] Help - WIRED Network unstable (reconnect/disconnect) after couple minutes"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by dbkungfu on 2008-03-28
Hi gurus

Recently after installing my 2nd ubuntu box that is a gutsy AMD64, 4gb RAM. I had been having this weird wired network disconnect/reconnect problems after couple of minutes.

Wired network is on static IP

*ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:1E:0B:32:75:78  
          inet addr:165.204.196.25  Bcast:165.204.196.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:bff:fe32:7578/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2394636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1314145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1755923049 (1.6 GB)  TX bytes:94260433 (89.8 MB)
          Interrupt:19 


*lspci *
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)

*ethtool -a*
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes


read all the related on this forum doesnt to fine anyone with this kind wired issues.
so I was hoping this is due to some incorrect setting in my eth0 setup

just case, my workstation is a HP xw4550 & the ethernet connector is on board.

thnx in advance ...

db

---

### Post by kpsmith on 2008-03-28
Hi

I wouldn't of thought that an intermittant connection would be caused by a faulty config - you either can connect or you can't even with a duplex mismatch, however looking at the config file it's set to auto negotiate so won't be an issue.

I would check the following before looking at the config further

1)Re-seat the ethernet patch lead at both ends to make sure tha connection is good
2) Failing the above replace the patch lead.
3) Failing this try the patch lead with a known working PC this will further isolate if (a) it is the lead (b) it might be the ehternet port on your PC.
4) Try using an ethernet card incase it's the port on the PC
5) If none of the above work it's either an issue with the config (no sure what though from looking but im no linux expert) or the port on the router/modem is at fault.

I'd make sure my h/w was set up right first and hit the config last in this case. As a network engineer the amount of issues that I see like this turn out to be h/w related normally a lead that needs re/seating/replacing or a knackered on board ethernet port.

---

### Post by dbkungfu on 2008-03-30
Hi kpsmith

changed the cable. Doesnt seem to help. If there a problem with the cable, one thing I still dun get it is how come the network keep on disconnect & reconnect recursively ... & not totally disconnect. :(

anyway, I am checking with my network engineer to see whether they enforce some form of control per mac address.

thnx

---

### Post by dbkungfu on 2008-04-02
hi

just to close this. 

discovered that it is due to :

1. incorrect cable type. changed cat5 to cat6. been monitor for couples of day. seems stable so far.
2. plus modified the dhclient.conf to embed fix dns servers IP

---

