---
title: "Problem with RA 2500 chip wireless card"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by kidamnesiac on 2007-01-16
Hi, I run 6.10 Ubuntu and am having some problems getting my generic RT2500 driver based card to connect to my network.
It worked with just a simple update in Kubuntu but I switched and have not been able to connect at all. 
The problem is that it cannot make a connection to the router. It sees the router, the network, and is able to judge signal strength. It sends packets to the router but is unable to recieve them as evidenced by connection properties. When i use the K wireless manager to connect, the network appears but when i click on it the message connection failed immediately appears. Using KWifimanager says that the network is out of range. 

Here is my ifconfig:
ra0       Link encap:Ethernet  HWaddr 00:0E:2E:AB:A2:4A  
          inet6 addr: fe80::20e:2eff:feab:a24a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3560985 (3.3 MiB)
          Interrupt:10 

and iwconfig:
ra0       RT2500 Wireless  ESSID:"Qwert"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any help would be greatly and forever appreciated, I use this forum all the time as a reference but this is the first occasion, after 4 months of (k)ubuntu use that I've had a problem I cant fix myself. 
Thanks

---

### Post by discord on 2007-01-17
I dunno but try 
sudo iwlist ra0 scan
sudo iwconfig ra0 essid "name"

there are other options such as setting the mac address of the ap. Also try rebooting the router.

---

### Post by kidamnesiac on 2007-01-17
It sees the network and knows to connect to QWERT.
A friend who knows linux inside and out and runs kubuntu spent a little time trying to configure the MAC address to no avail. It is also definitely not the router, it's been reset a few times. 
Unfortunately my friend doesn't have infinite time to play with it.
The worst part is that the cd that came with the card doesn't have a .INF file so I can't even try ndiswrapper!
The more I search the more this seems to be a problem for a LOT of people in ubuntu :(

---

### Post by kidamnesiac on 2007-01-17
bump

---

### Post by kidamnesiac on 2007-01-17
after doing the module install using module-assistant over again, I cannot find networks anymore and I get the message that my cards radio is not on. 
Help is truly appreciated.

---

### Post by Fruhwirth on 2007-01-17
I have the RA2500 chipset and had problems with it in my first install of Ubuntu Dapper. I had initial trouble with it, started googling, began to tinker and I think I made things worse (these were my first days on anything besides windows/mac systems).  Eventually I got it to work but I had no idea why it had begun to work.  I was using rutilt as a gui but it didn't seem to work well. For example, when I went to the coffee shop, it would not  connect to the new network.

Well, for unrelated reasons, I completely reinstalled Dapper.  This time around, I instaled wlassistant (wireless assistant) from Add/Remove Programs and everything works the way it is supposed to, i.e., without any effort at all.  I haven't had to do anything to configure the RA2500!  It just works. I have only tried it on DHCP networks, so don't know if it will work on other configurations as easily as it did my home network.

---

