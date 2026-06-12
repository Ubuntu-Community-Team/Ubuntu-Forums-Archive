---
title: "[SOLVED] Wireless USB network adapter not working"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Dragonfi on 2007-09-09
I Instaleed Xubuntu on my older computer , the installation went fine ,but I cannot get my Hama Wireless LAN USB adapter (00062764) working. I'm working on it around 15 hrs now. 

The page I found for the USB thing: ( I cannot found anything in english)
           [http://www.hama.de/portal/articleId*128327/action*2563/searchMode*1/bySearch*00062764](http://www.hama.de/portal/articleId*128327/action*2563/searchMode*1/bySearch*00062764)

I ried it on my Wother computer with Win XP ,it worked well with it 's driver from it's disc (has only Mac and Win drivers on it ).
Tried with and without WEP key.
Doing a troubleshooting guide from help.ubuntu.com.

The info I gathered and think that can be usefull:
///////////////////////////
lsusb :

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 13fe:1a20  
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000  

lshw :

   *-usb:1
                   description: Generic USB device
                   product: 802.11 bg WLAN
                   vendor: Ralink
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=rt73usb maxpower=300mA speed=12.0M
ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:50:BF:5A:9D:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:50:BF:5A:9D:20  
          inet addr:169.254.5.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21064 (20.5 KiB)  TX bytes:21064 (20.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:C8:7F:7A  
          inet6 addr: fe80::20e:2eff:fec8:7f7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:52332 (51.1 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:0E:2E:C8:7F:7A  
          inet addr:169.254.7.33  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-C8-7F-7A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
/////////////////////

I would start using Linux , but first I want to have this wireless connection.
I hope you can help me fast, maybe I shoul simply buy a 20 m long cable :(

P.S. : Sorry for the bad grammar.

---

### Post by noob12 on 2007-09-09
You should look at this:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by Dragonfi on 2007-09-10
Thank You, it helped  ,but now I'm rebooted the system and cannot get the connection working.
I have no idea what went wrong , It should start automatically becaues I edited the interfaces file,bit I cannot even get IP manually (there is some sort of connection, there is 61 signal strength and some recived /sended packages).
I go back and continue, maybe I missed a detail somewhere.

---

### Post by noob12 on 2007-09-10
You should try posting on that thread for help.

---

### Post by Dragonfi on 2007-09-12
Thank you for redirecting to the guide, it solved the problem.

---

