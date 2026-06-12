---
title: "wifi with 8.10"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by hellomoto on 2009-03-08
hey guys, just upgraded from 8.04 to 8.10. Install was great.

I was most impressed that this was the first edition to recognise my wifi card out the box.

Whilst it was good and connected to the network. The reception was poor and eventually i lost my connection to the network. I know that the signal is great to my PC. As I never had problems with 8.04 and I dual boot into windows on the same PC and I get 100% reception with the same wifi card. 

Is there any way I can disable the current driver used by 8.10 for my wifi card so I can try use Ndiswrapper like i have done with 8.04.

Also is there any way i can chosse what DNS servers I use in 8.10. 

thankyou in advance

---

### Post by Kareeser on 2009-03-08
The wireless driver should be listed in System -> Hardware Drivers.

You can disable "wl" from there, and use ndiswrapper to install the Windows driver of your choice :)

---

### Post by hellomoto on 2009-03-08
many thanks. that was very helpfull! :D

---

### Post by hellomoto on 2009-03-08
hmmm its not listed in there. 

Here is some more info: 

```

02:09.0 Ethernet controller: Belkin Device 700f (rev 20)

```

```

eth0      Link encap:Ethernet  HWaddr 00:50:8d:b3:fd:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28900 (28.9 KB)  TX bytes:28900 (28.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:32:bd:28  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:182822340 (182.8 MB)  TX bytes:5679058 (5.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-32-BD-28-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

