---
title: "Wireless Troubles"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by jwdresser on 2008-11-05
after upgrading from 8.04 to 8.10 my network manager doesnt list possible network connections.

but if I run:

iwpriv wlan0 network_type g
iwconfig wlan0 essid "any" 
ifconfig wlan0 up
iwlist wlan0 scan

everything works and thats fine with me, as long as it works

my question is whats going on here and how can I make this work without having to do that every time I log in?

---

### Post by jwdresser on 2008-11-06
this method also sometimes connects to my neighbors wifi

help please

---

### Post by kagashe on 2008-11-06
> **jwdresser said:**
> after upgrading from 8.04 to 8.10 my network manager doesnt list possible network connections.

but if I run:

iwpriv wlan0 network_type g
iwconfig wlan0 essid "any" 
ifconfig wlan0 up
iwlist wlan0 scan

everything works and thats fine with me, as long as it works

my question is whats going on here and how can I make this work without having to do that every time I log in?For Network Manager refer to the [HOWTO]("http://ubuntuforums.org/showthread.php?t=970247")

> this method also sometimes connects to my neighbors wifi
There is a setting BSSID. Put the BSSID of your router here.

kagashe

---

### Post by jwdresser on 2008-11-06
how do I find my routers BSSID? all I can find is SSID.

when I follow the howto it still doesnt connect

---

### Post by kagashe on 2008-11-06
> **jwdresser said:**
> how do I find my routers BSSID? all I can find is SSID.

when I follow the howto it still doesnt connect
If you know the SSID put it correctly. The howto works only when your wirelss card is detected and configured as wlano or eth1 etc. Type
> ifconfig -a 
in the terminal and paste it here.

kagashe

---

### Post by jwdresser on 2008-11-07
eth0      Link encap:Ethernet  HWaddr 00:40:ca:ce:c6:9c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 3e:a4:a9:72:a5:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0c:76:ff:e4:42  
          inet6 addr: fe80::20c:76ff:feff:e442/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15758 (15.7 KB)  TX bytes:576 (576.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-76-FF-E4-42-34-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

here's a screenshot
[http://www.flickr.com/photos/32243017@N08/3010972156/sizes/o/]("http://www.flickr.com/photos/32243017@N08/3010972156/sizes/o/")

---

### Post by kagashe on 2008-11-08
> **jwdresser said:**
> how do I find my routers BSSID? all I can find is SSID.After setting up the connection (as you are already doing) type the following in the terminal:
> iwconfig wlan0What you find against "Access Point:" is the BSSID of the router (Beware it may be also your neighbour's) to which you are connected.

> when I follow the howto it still doesnt connectBecause there is no way to put the setting:
> iwpriv wlan0 network_type g
You can try the HOWTO after entering this command.

kagashe

---

### Post by jwdresser on 2008-11-08
I noticed that my wireless card was "unmanaged" when I ran nm-tool, did a search and followed this post [http://ubuntuforums.org/showthread.php?t=940558]("http://ubuntuforums.org/showthread.php?t=940558"). Got me back online.

---

