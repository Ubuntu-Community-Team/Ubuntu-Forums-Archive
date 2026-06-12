---
title: "DSL on ubuntu 7.10 CE not working, please help."
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Huggy on 2008-01-12
please excuse the mess. I copy and pasted the prompt lines from ubuntu 7.10 CE onto my usb stick then rebooted into Windows where I have internet and now I'm pasting them here. So they're not very clean and I don't really know how they're supposed to go. I just know none of th commands didn't work.

danika@mikayla-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:D8:70:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:03:47:D8:70:72  
          inet addr:169.254.7.20  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28273 (27.6 KiB)  TX bytes:28273 (27.6 KiB)



danika@mikayla-desktop:~$ pppoe
pppoe: Timeout waiting for PADO packets

danika@mikayla-desktop:~$ sudo pppoeconf

  Sorry, I scanned 2 interfaces, but the Access            &#9474;          
&#9474; Concentrator of your provider did not respond. Please    &#9474;          
&#9474; check your network and modem cables. Another reason      &#9474;          
&#9474; for the scan failure may also be another running pppoe   &#9474;          
&#9474; process which controls the modem.

I hope some of those commands told you something. I'm a complete noob but I'm not completely dumb. It acts like it can't even see my network card. When I open the network tools thing, you know the drop down bar that usually has your interfaces in it like eth0 and so on...well it has nothing, and unlike the old ubuntu I had I see nothing where you can select PPPOE specifically for my DSL interet. It's all just auto detect DHCD. I tried a static address, but when you can't even see the router it doesn't do any good.

Please help me someone. I'm totally lost, and this is my daughters computer. She needs it for school (homeschooled via interent courses).

---

