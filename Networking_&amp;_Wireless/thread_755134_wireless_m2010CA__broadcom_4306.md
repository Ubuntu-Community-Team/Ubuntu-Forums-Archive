---
title: "wireless m2010CA  broadcom 4306"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by csa on 2008-04-14
Hi all...

I would really appreciate some help...  I just can't get my wireless to work.  I have a Compaq (HP)  M2010CA, with a Broadcom 4306 Network controller.  I have installed Ubuntu Gutsy 7.10, in all the hard drive (that is... I have no Windows installed in my computer).

Everything's working perfectly, except for the wireless card.  I am now using a wired connection but before, with Windows XP I could get wireless internet.

If I put iwconfig in terminal, I get the following:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and if I put ifconfig, I get this:

eth0      Link encap:Ethernet  direcciónHW 00:90:4B:AD:21:5F  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:e0204000-e0206000 

eth1      Link encap:Ethernet  direcciónHW 00:C0:9F:89:F9:A6  
          inet addr:192.168.1.68  Difusión:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe89:f9a6/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:7243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5274 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:5750225 (5.4 MB)  TX bytes:720232 (703.3 KB)
          Interrupt:18 Base address:0x6800 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)

I tried using ndiswrapper, and the driver bcmwl5.inf, and apparently it finds the hardware, but after I do the whole process... I still get no wireless.

If I click on network manager, it doesn't show any wireless signals available, as though there was no wireless internet around, but with another computer, I find like six wireless internet available...

I would really really appreciate any type of help I can get, cause I've run out of ideas now...

---

