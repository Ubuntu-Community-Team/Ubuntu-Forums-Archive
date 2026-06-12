---
title: "Compaq 6510b Intel 3945"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by dgrammer on 2008-03-31
Have a brand new HP 6510b laptop. Intel wireless works fine in m$ windows xp. Install Ubuntu 7.10 and the new beta 8 with the same problem. I can turn on the wireless radio and the network manager sees the card and sees several access points around me. But I cannot connect to them. The one I am trying to connect to is a Cisco 1231. The log says it authenicates but then de-authenicates. I believe it is because it cannot pull an IP address through DHCP. Other laptops work fine on the same AP. I tried to assign a static IP address to the wireless card and then it will connect to the AP, but no network traffic is going through. I cannot ping the gateway or anything else. 

Any Ideas?

THanks

---

### Post by Eiríkr on 2008-03-31
This might be a driver issue.  To help diagnose, please open a terminal, then type in each of the following and post the results to this thread:
```
ifconfig
iwconfig
cat /etc/network/interfaces
sudo /etc/init.d/networking restart
```

Cheers,

Eiríkr

---

### Post by dgrammer on 2008-03-31
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1a:4b:60:0f:c9  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe60:fc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:557716 (544.6 KB)  TX bytes:85937 (83.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81684 (79.7 KB)  TX bytes:81684 (79.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:b4:ff:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-B4-FF-E8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cat /etc/network/interfaces

auto lo
iface lo inet loopback


sudo /etc/init.d/networking restart

* Reconfiguring network interfaces... 



Thanks
Daryl

---

### Post by dgrammer on 2008-03-31
?

---

### Post by Eiríkr on 2008-03-31
Looks like the only interface actually listed in your interfaces file is the loopback.  Try running ifconfig after restarting the networking service, and let us know what interfaces are shown.

Cheers,

Eiríkr

---

### Post by dgrammer on 2008-03-31
that doesnt make any sense as I was plugged into the network via copper when I did that and used that computer to post.

---

### Post by Eiríkr on 2008-03-31
Than you for the clarification, that wasn't a given to start.  Part of my confusion is that, as far as I've been given to understand, restarting the networking service should only bring up those interfaces listed in the interfaces file.  This implies that something else is going on in your system.  Anyone else have any ideas?

Cheers,

Eiríkr

---

### Post by dgrammer on 2008-04-01
Interestingly I was playing around and got 8.04 to work with another AP out there. Not sure what brand it is but it works. So apparently it is some kind of compatibility issue with the Cisco 1231AG and the Intel 3945. I took all security off the AP just to make sure. I am updating the firmware now to see if there are any differences. Does anyone know of any compatibility issues there?

---

