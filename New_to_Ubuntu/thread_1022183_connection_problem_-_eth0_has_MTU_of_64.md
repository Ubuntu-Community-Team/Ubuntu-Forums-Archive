---
title: "connection problem - eth0 has MTU of 64"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by petterwr on 2008-12-26
dell inspiron 2200 - installed ubuntu 8.10 and deleted win xp. (everything worked on the old os but was extremely slow)

Got it up and working, much faster than before, except for the internet connection. 

Tried sudo pppoeconf and it found eth0 and pan0 but got the following message:

"Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also b e  another running ppoe process which controls the modem."

No other option than to click ok.

In the terminal when i click ok the followin text has appeared:

"Interface eth0 has MTU of 64 -- should be 1500. You may have serious connection problems." x2

No connections work.. If anyone can help me solve this quickly you´d make me very happy :)

---

### Post by zvacet on 2008-12-27
Whitch net card do you use?

---

### Post by petterwr on 2008-12-28
I´m not sure what netcard it is.. looking at some [schematic photos]("http://support.dell.com/support/edocs/systems/ins2200/en/SM/system.htm#1084976") from dell it seems like its a part of the motherboard as far as I can see (the ethernet plug is between the modem plug and the usb plugs which are to the far right when seen from the front). 

It´s a 10/100 Ethernet card according to dell´s homepage but they dont give any more detailed information. 

They recommend their own driver: (R)PRO/100 VE Network Connection 
which can be found [here]("http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=5&impid=-1&servicetag=&SystemID=INSPIRON+2200&hidos=NAA&hidlang=en&TabIndex=") for windoze and MS-dos - they dont have any options for anything else.

---

### Post by Michael.Godawski on 2008-12-28
hi,

can you please post the outputs of these commands:

```
ifconfig
sudo lshw -C network
```

---

### Post by petterwr on 2009-01-03
Thanks for your reply :)

Answering took me a while since its my brothers computer and he's living abroad.. Anyway here it is:
> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:1b:fe:38  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3550 (3.5 KB)  TX bytes:2907 (2.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)


> 
sudo lshw -C network
[sudo] password for terje: 
  *-network               
       description: Ethernet interface 
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 03 
       serial: 00:12:3f:1b:fe:38 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 42:c8:ef:ad:cd:7d 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 


---

