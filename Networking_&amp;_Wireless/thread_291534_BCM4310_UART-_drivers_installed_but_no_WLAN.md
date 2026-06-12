---
title: "BCM4310 UART- drivers installed but no WLAN"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by velozoom on 2006-11-02
I have an hp dv9000 laptop running Edgy,  I used FWcutter and then installed the drivers for the card.  The card now shows in the network tools but I still can not get it to work.  I have tried many suggestions I have found on the forum but have had no luck.  

it is my understanding that I don't need ndiswrapper if I have extracted the drivers using fwcutter.  Is this correct?

The NIC shows in network tools after installing the driver but the config button is sometimes blurred out, and sometimes not.  I am sure my network security info is correct and I've even tried make my WAP wide open and tried that.....still nothing.  ](*,) 

I am new enough to Linux that I don't really know where to start looking.  

ANy help is appreciated.  
```

$ ifconfig -a 


eth0      Link encap:Ethernet  HWaddr 00:16:36:9E:BD:5C  
          inet addr:xx.xx.xx.xx  Bcast:xx.xx.xx.xx  Mask:255.255.224.0
          inet6 addr: fe80::216:36ff:fe9e:bd5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34041312 (32.4 MiB)  TX bytes:3476846 (3.3 MiB)
          Interrupt:10 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:E7:5F:F2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6370 (6.2 KiB)
          Interrupt:255 Base address:0x8000 


FYI- IP info on eth0 was modified


```

---

### Post by velozoom on 2006-11-03
Any help or suggestions?  :)  

I've done the searching and I'm really not sure where to go from here.....

---

