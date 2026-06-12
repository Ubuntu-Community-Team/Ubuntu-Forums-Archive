---
title: "No wired internet all of a sudden"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by henkeb on 2008-10-10
Hi guys. Having a strange problem, I´ve always been using wired internet for my ubuntu hardy laptop, roaming mode just as it came, never touched it, straight from the jack, no router. Since two days, it just wont work, network manager says I´m connected but I can´t visit any websites or ping anything. If i check connection details ip is 0.0.0.0, so is mask and everything else. I´m really at a loss here, could it have been an update that broke it? Internet works on my other computer so it´s not the connection. Would really appreciate any help on this one.

Cheers.

---

### Post by Iowan on 2008-10-10
Post results of **ifconfig -a** and contents of **/etc/network/interfaces**. I won't bore you with how-to details unless you ask. ;)

---

### Post by henkeb on 2008-10-14
I reinstalled ubuntu and got it working yesterday, but today its the same thing. Seems like it works from time to time. Here are the results from ifconfig -a and /etc/networking/interfaces


ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:15:af:61:6d:45  
          inet addr:192.168.50.115  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe61:6d45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1657138 (1.5 MB)  TX bytes:161567 (157.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1d:92:4d:43:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4764 (4.6 KB)  TX bytes:13218 (12.9 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75482 (73.7 KB)  TX bytes:75482 (73.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-61-6D-45-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8112 errors:0 dropped:0 overruns:0 frame:514
          TX packets:1491 errors:54 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:1726358 (1.6 MB)  TX bytes:207889 (203.0 KB)
          Interrupt:18 


Contents of /etc/network/interfaces:
auto lo
iface lo inet loopback

---

### Post by superprash2003 on 2008-10-14
you seem to be getting an ip 192.168.x.x .. try pinging a website like google by typing ping google.com

---

### Post by Mazin on 2008-10-14
@superprash
i think he's asking about wired internet

The network information seems to show that it's working.  Try first disconnecting from your wireless Internet.  Then, disable your wired internet connection
```
sudo ifdown eth0
```
and then enable it again
```
sudo ifup eth0
```
and see if it gives any information. It should try to get an IP address from your router, with something like:
```
Listening on LPF/eth1/00:18:56:99:8e:be
Sending on   LPF/eth1/00:18:56:99:8e:be
Sending on   Socket/fallback
etc.

```

If it can't get an IP address, that could be a problem with your router.

---

### Post by Iowan on 2008-10-14
If you're using Network Manager, it seems to want only one interface active at a time.  Since ath0 is getting an address, eth0 probably won't.  If manually "ifup-ing" works, you can consider adding a section in **/etc/network/interfaces** to automatically set up eth0.  One cavaet - both interfaces (ath0 and eth0) shouldn't have addresses in the same subnet (192.168.50.x).

---

### Post by henkeb on 2008-10-15
Thanks a lot for the answers. Already tried ifdown/ifup, that didn't do the trick for me and the problem can't be router-related since I don't use one. It works fine now though, and when it doesn't, it seems that if I change from roaming to DHCP it works, and if I change back to roaming it still works. Never had any problems with having both eth0 and ath0 active so it's really strange, plus it's worked out of the box and had worked for 6 months and now all of a sudden it's acting up.

---

