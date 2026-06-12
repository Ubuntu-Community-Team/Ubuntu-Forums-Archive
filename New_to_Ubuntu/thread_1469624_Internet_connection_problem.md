---
title: "Internet connection problem"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-05-02
Here is my problem I currently have TWO laptops side by side. BOTH run Ubuntu. One is connected via wi-fi to the Internet the other will not connect. I tried to uninstall the recognized wi-fi and reinstall, make sure password was correct etc. The PC claims it is connected to the modem which it does recognize and it gives a connection strenght 42% +/-. It actually says "Wireless network connection 'Auto Thomson 81E5AB' active: Thomason81E5AB (38%). So it connects to the modem and currently can see it but not to the internet. I checked password several times and rebooted. My other PC is connected just fine. What gives? Why will it not recognize the password or otherwise connect.

---

### Post by senormoll on 2010-05-02
Can you open up the terminal, type ifconfig then enter, and post the output?  I don't think I'd be able to help but whoever can will almost certainly ask for that information :)

---

### Post by HermanAB on 2010-05-02
Well, for a network connection to work, you need a number of things to be configured correctly:
Physical connection (wired or wireless)
IP Address
Network Mask
Gateway Address
Default Route

So the wireless connection is only part of the problem.

Verify you IP Address and Netmask with 'ifconfig' and verify the default route with 'route'.

Ifconfig shows the network connection name - probably 'wlan0'.  Use that to rerun the program 'dhclient' to force your router to give the rest of the information:

$ sudo ifconfig

$ sudo dhclient wlan0

If all the internet gods are smiling kindly upon you, then your network connection will now work.

---

### Post by Amockineuropa on 2010-05-02
eth0      Link encap:Ethernet  HWaddr 00:26:22:28:b5:d4   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:28  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 0c:60:76:57:ae:f4   
           inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::e60:76ff:fe57:aef4/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:1766 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:537 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:144586 (144.5 KB)  TX bytes:55563 (55.5 KB)  
 

 wmaster0  Link encap:UNSPEC  HWaddr 0C-60-76-57-AE-F4-35-37-00-00-00-00-00-00-00-00   
           UP RUNNING  MTU:0  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Amockineuropa on 2010-05-02
I tried the dhclient wlanO (with a capital O) got permission denied

---

### Post by Amockineuropa on 2010-05-02
Seems my IP Address: 192.168.1.64
                  Netmask:     255.255.255.0
                  Inet6 addr    is given above

---

### Post by Amockineuropa on 2010-05-02
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0  
 link-local      *               255.255.0.0     U     1000   0        0 wlan0  
 default         speedtouch.lan  0.0.0.0         UG    0      0        0 wlan0

---

