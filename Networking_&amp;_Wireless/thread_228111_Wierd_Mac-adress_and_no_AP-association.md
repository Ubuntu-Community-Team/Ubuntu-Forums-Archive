---
title: "Wierd Mac-adress and no AP-association"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Kosika on 2006-08-02
Hello. I'm having this annoying problem that I can't seam to fix.
I'm quite new to linux and are now running Ubuntu 6.06.
I have an Netgear WG311T wireless adapter and the drivers are the one thats standard in Dapper Drake.
When I have an fresh install all works good, I can connect to the net etc all works good.
But I'm altso experimenting with sniffing packets with airocrack etc. Then afterwards internet stopps working (I'm not trying to access internet while sniffing but afterwards, even tested rebooting).
The first time I started to test sniffing I uppdated to the latest Madwifi driver (0.9.1) and then got this problem, after several hours of scratching my head I finaly reinstalled Ubuntu and all was alright utill I started exprimening with sniffing again, but I havent tuched the drivers.
Here is a Dump from Ifconfig and iwconfig with a fresh install:

duke@Bollibompa:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:2C:BD:F7
          inet6 addr: fe80::214:6cff:fe2c:bdf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:1872 dropped:0 overruns:0 frame:1872
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:14492 (14.1 KiB)  TX bytes:6282 (6.1 KiB)
          Interrupt:11 Memory:f8b20000-f8b30000

eth0      Link encap:Ethernet  HWaddr 00:01:80:36:CA:1F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1556 (1.5 KiB)  TX bytes:1556 (1.5 KiB)

duke@Bollibompa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Bjornby_1"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:60:1D:F1:23:AB
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/94  Signal level=-1 dBm  Noise level=-95 dBm
          Rx invalid nwid:111  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

and after a while when it stopped working it looked like this:

duke@Bollibompa:~$ ifconfig
ath0      Link encap:UNSPEC  HWaddr 00-14-6C-2C-BD-H2-20-73-00-00-00-00-00-00-00-00
          inet addr:193.201.17.73  Bcast:193.201.17.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1090 errors:5149 dropped:0 overruns:0 frame:5149
          TX packets:1032 errors:258 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:1094806 (1.0 MiB)  TX bytes:70195 (68.5 KiB)
          Interrupt:11 Memory:f89e0000-f89f0000

eth0      Link encap:Ethernet  HWaddr 00:01:80:36:CA:1F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12517 (12.2 KiB)  TX bytes:12517 (12.2 KiB)


## So then I try to change the mac with ifconfig: 


duke@Bollibompa:~$ sudo ifconfig eth0 hw ether 00:1c:44:23:34:1a
SIOCSIFHWADDR: Device or resource busy
duke@Bollibompa:~$ sudo ifdown ath0
duke@Bollibompa:~$ sudo ifconfig ath0 hw ether 00:23:23:42:ae:2e
SIOCSIFHWADDR: Invalid argument
duke@Bollibompa:~$ sudo ifup ath0 <<<<<When writing this it takes around 60 sec for it to complete

duke@Bollibompa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"Bjornby_1"
          Mode:Monitor  Frequency:2.442 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:19  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:306   Missed beacon:0

sit0      no wireless extensions.

duke@Bollibompa:~$

#### Here I tested changing mac with "GNU macchanger"

Result:  
duke@Bollibompa:~$ ifconfig -a
ath0      Link encap:UNSPEC  HWaddr 00-00-8F-E0-78-FD-20-03-00-00-00-00-00-00-00-00
          inet addr:193.201.17.73  Bcast:193.201.17.255  Mask:255.255.255.0
          BROADCAST  MTU:1500  Metric:1
          RX packets:1363 errors:15354 dropped:0 overruns:0 frame:15354
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:146841 (143.3 KiB)  TX bytes:30105 (29.3 KiB)
          Interrupt:11 Memory:f89e0000-f89f0000

##
So, what can I do, please be patient, I'm new to this stuff.

BTW: I'm writing this post via windows and the same wireless card with no problems.

Thanks for any help!

---

### Post by Paloseco on 2006-08-08
sudo ifconfig ath0 down
sudo ifconfig ath0 hw ether 00:1c:44:23:34:1a
sudo ifconfig ath0 up

If you are using madwifi drivers you can create multiple interfaces  for the same hardware device, while wifi0 is the "real" interface ath0, ath1, etc are virtual interfaces so if you have various of them you could have problems.

[http://madwifi.org/wiki/ngFeatures#VAPsandwlanconfig](http://madwifi.org/wiki/ngFeatures#VAPsandwlanconfig)
[http://madwifi.org/wiki/UserDocs](http://madwifi.org/wiki/UserDocs)

In the same line:
ifconfig wifi0 down hw ether xx:xx:xx:xx:xx:xx
ifconfig wifi0 up

---

