---
title: "Ethernet cable connected but not working - Ubuntu 16.04 LTE"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by uyohn on 2016-08-03
Hello

I installed Ubuntu on my laptop and ethernet connection isn't working. Wireless fortunately is.
When I click at the Connections icon on top panel, it says "Ethernet network disconnected" but in windows 10 on this same laptop it's working.
output of ```
ifconfig
``` is: 
```
enp1s0    Link encap:Ethernet  HWaddr 28:d2:44:7e:bb:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:116074 (116.0 KB)  TX bytes:116074 (116.0 KB)


wlp2s0    Link encap:Ethernet  HWaddr b8:ee:65:aa:73:d6  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eb81:7f9d:ccbe:8642/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21580911 (21.5 MB)  TX bytes:2384968 (2.3 MB)

```

I was looking for solution but nothing worked. Thank you for help
--uyohn

---

### Post by claracc on 2016-08-03
Perhaps you have a known bug in ubuntu 16.04 with wired net.

You can edit the file /etc/network/interfaces ( use gksudo gedit /etc/network/interfaces ), and see that you have commented with # sign at the begining  two of the lines, as it is shown below :

#iface eth0 inet dhcp

#auto eth0

So, your interfaces file will show as :

```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth0

```

Then save the file and try to connect the wired net.

---

### Post by claracc on 2016-08-03
I forgot to say, after changing interfaces file, you reboot the machine and the wired connection perhaps work.

---

### Post by uyohn on 2016-08-03
Thank you for such quick reply.

I commented those lines, but still not working.

---

### Post by claracc on 2016-08-03
¿Have you rebooted the pc?. Then try to connect the wired net.

Perhaps the wire you use is broken. Could you try with other wire?

---

### Post by uyohn on 2016-08-03
Okay, it's wokring now. I don't know why.
My laptop is connected via a Switch, so i tried to connect it directly to the main router - and it worked. Then I connected it back to the switch and it's working. 

Thank you very much for your help.

---

### Post by claracc on 2016-08-03
Glad you got your problem fixed.

Please, mark the thread as "solved" with thread tools in the upper right part of the page.

---

