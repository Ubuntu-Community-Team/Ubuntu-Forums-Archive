---
title: "Can't get my printer to print wirelessly"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by Steve_and_Becky on 2014-03-21
We have a brother printer, model no.MFC-J4710DW.  It was working just fine before we switched internet service providers.  We have Ubuntu CE 12.04 installed on our computers and we were able to print with that printer just fine.  Our printing was wireless.  Well, we just changed internet providers.  We can get our Brother printer to print with our Ubuntu computer if it is hooked up with usb cable, but it seems to have lost its ability to print wirelessly.  I suspect that there is a setting I am missing somewhere, but I can't figure out what setting I am missing nor how to configure our printer so that it will communicate with our computer.  We really want to print without a cable so that we can carry our computer with us.  We have a laptop.  I would sure appreciate it if someone could guide me along with this!  We have DSL, and we have a wireless modem, not a router.  Witht the wireless modem we are able to get several computers to hook to our network wirelessly.  I hope someone can help me with this.  I haven't been able to find anything on the forums that applies to what I am dealing with here that works.

Becky

---

### Post by tgalati4 on 2014-03-21
Open a browser:  [http://localhost:631](http://localhost:631)

Since CUPS (the printing service used in Linux) uses port 631 to communicate, it is possible that your new router is blocking port 631.  You will have to log in to the router and dig through the settings to poke a hole in that port.

It's also possible that the network settings on the printer are incorrect.

Open a terminal and post the output of:

```
ifconfig
```

And write down all of the network settings on the printer and post them as well.

---

### Post by Steve_and_Becky on 2014-03-22
First, thanks for the guidance.  Second, here's what running the ifconfig told me:

   eth0      Link encap:Ethernet  HWaddr 00:1c:25:9a:35:06   
           inet addr:10.8.16.1  Bcast:10.8.16.0  Mask:255.255.255.0 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 

           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

           Interrupt:20 Memory:fc000000-fc020000  


  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:2866 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2866 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:234139 (234.1 KB)  TX bytes:234139 (234.1 KB) 
 

  lxcbr0    Link encap:Ethernet  HWaddr 4e:dc:4b:c7:5d:72   
           inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0 
           inet6 addr: fe80::4cdc:4bff:fec7:5d72/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:155 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:22936 (22.9 KB) 


  
 wlan0     Link encap:Ethernet  HWaddr 00:21:5d:98:3c:dc   
           inet addr:192.168.254.42  Bcast:192.168.254.255  Mask:255.255.255.0 
           inet6 addr: fe80::221:5dff:fe98:3cdc/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:38729 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:26858 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:13900690 (13.9 MB)  TX bytes:2800588 (2.8 MB) 

These are the printer settings that the printer printed out for me when I set it up to connect to our internet connection:

Network Name (SSID)    Sessions     
Hardwware Address (MAC)  9c:2a:70:07:66:b3
Communication mode         Infrastructure
Authentication Type            WPA/WPA2-PSK
Encryption                        AES
Network Channel               8
<Network Search (Ch, Signal, SSID)>
8 , 7 ,  Sessions

The network settings do seem different than what they were when we had wireless instead of DSL.  With our wireless, it was 192.168.etc.  With the DSL, it doesn't seem to set the printer up that way, if that makes sense.  I am trying to explain the best I can, but at the same time I am confusing myself trying to explain it.

My computer's network settings(not the printer's):

ip Address  192.168.254.42
Broadcast address  192.168.254.255
Subnet adderss      255.255.255.0
Default address      192.168.254.254
Primary address     192.168.254.254

---

### Post by alan_martin2 on 2014-10-10
I have just migrated from Windows XP to Ubuntu 14.04 and have the same problem I.e. Can print using USB cable but my laptop can't see my DCP-J140W Brother printer wirelessly. Did you find a solution?

---

