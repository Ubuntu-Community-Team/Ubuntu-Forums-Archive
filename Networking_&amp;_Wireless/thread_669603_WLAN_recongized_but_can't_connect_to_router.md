---
title: "WLAN recongized but can't connect to router"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by okoeth on 2008-01-16
Hi,

I have installed ubuntu 7.10 on my somewhat aged desktop and tried to connect to my home WLAN with an acer WLAN-G-US1 USB adaptor. The hardware is apparently recognized, it shows up in the device manager as well as network-admin and lsmod also shows that a zd1211rw driver has been loaded.

Nevertheless i'm unable to connect to my WLAN router (arcor easybox 300 WLAN). As recommended, I turned WEP/WPA off on the router during my connection experiments.
With the wireless set to roaming mode in network-admin, I get the following output from iwconfig:

eth1      IEEE 802.11b/g  ESSID:"eisbaer-wlan"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:19:12:A2:C1   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
The access point is in fact the MAC of my router, and the ESSID matches my home WLAN. 
ifconfig does not list an IP address:

eth1      Protokoll:Ethernet  Hardware Adresse 00:11:E2:02:5A:B6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 b)  TX bytes:2646 (2.5 KB) 

When I click on the ESSID of my WLAN listed in the network connections menu, the icon spins for a while and then displays "no connection" again.

I then tried setting the ESSID explicitly in network-admin instead of roaming mode. After rebooting, the output of iwconfig has changed to

eth1      IEEE 802.11b/g  ESSID:"eisbaer-wlan"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
(btw, I had also changed the router to use standard channel 6 at that point, which it seems to have picked up)
ifconfig now lists an additional device

eth1:avah Protokoll:Ethernet  Hardware Adresse 00:11:E2:02:5A:B6  
          inet Adresse:169.254.6.210  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          
but I still have no connection and can't ping anything. The IP also appreas invalid. (Btw, the router DHCP would have assigned a 192.168 address, and the router did not log any connections from that machine)

I took a look at section 3.3 of [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
but it didn't seem to help here. As recommended, I tried to set the bit rate to 11Mbps explicitly, but got the following error

Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device eth1 ; Operation not permitted. 
    
It seems I'm stuck here. Do you have any suggestions what to try next or where to look for further help?

Thanks for any assistance,

Oliver

---

### Post by melopsittacus on 2008-01-16
Hello, try enabling broadcast SSID in your router. I was able to connect to my wireless router only after enabling it. I am using another type of wireless router/card though, so I am not sure this is the solution.

---

### Post by kegobeer on 2008-01-16
> **melopsittacus said:**
> Hello, try enabling broadcast SSID in your router. I was able to connect to my wireless router only after enabling it. I am using another type of wireless router/card though, so I am not sure this is the solution.

That's how I was finally able to connect to my wireless network.  I have no idea why this makes any difference.

---

### Post by melopsittacus on 2008-01-17
Yes, it is quite weird. But if you have WPA enabled, I do not think it matters too much.

---

### Post by okoeth on 2008-01-23
Thanks for the suggestion, but that doesn't help, since I did already have SSID broadcast enabled -- and apparently the SSID was picked up correctly, because it did show in the roaming connection menu before I had configured it anywhere explicitly.

---

### Post by Hightide on 2008-01-23
Hi

Gilf suggests  a way of trying to sort out wireless problems. It may be useful

[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

:)

---

