---
title: "How to set my laptop as an AP?"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by aubrey on 2006-09-14
Hi all,

I want to set my laptop(DELL-LATITUDE-D610) as an AP. But I'm blocked at the beginning.

Here is my wireless card type:
=====================================================
aubrey@ubuntu-dapper:~$ lspci | grep Wireless
0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
=====================================================

And iwconfig result:
=====================================================
aubrey@ubuntu-dapper:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"CTC"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:60:B3:18:8D:72
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-43 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:23   Missed beacon:0
=====================================================

The wireless device "eth1" can be set to "managed" and "ad-hoc" mode, but when I set it to "master" mode, I got the following error:
==================================================
aubrey@ubuntu-dapper:~$ sudo iwconfig eth1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
==================================================

I don't know what I should do next, really apprecidate any suggestion.

Thanks a lot.
-Aubrey

---

### Post by trubblemaker on 2006-09-14
what's 
```
 iwlist scan eth1 
``` tell you ? can you post it here?  after your iwconfig looks like it does as you posted here what's the output of running 
```
 sudo dhclient eth1 
```

---

### Post by aubrey on 2006-09-14
First command result:
====================================================
aubrey@ubuntu-dapper:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:16:C8:17:EC:50
                    ESSID:"ADIWLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=84/100  Signal level=-46 dBm
                    Extra: Last beacon: 24ms ago
----snip----
====================================================
The second command seems not make sense to me. Because I want to take my laptop as a dhcp server.
Anyway, the running result is as follows:
=============================
aubrey@ubuntu-dapper:~$ sudo iwconfig eth1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
aubrey@ubuntu-dapper:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0e:35:e8:39:51
Sending on   LPF/eth1/00:0e:35:e8:39:51
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by trubblemaker on 2006-09-14
Sorry I was reading another forum and replied here, my bad. 
Somethings to think about even though I haven't done this before. How are you getting your internet signal? you want to just use the one network card or is this laptop wired aswell?  

Normally a wired router requires two nics one for the Internet, one for the Network.  

I took a quick look through synpatic for a package for you try a search on routing and I think you'll find what you want.

---

### Post by aubrey on 2006-09-15
Of course there are two nics on my laptop. One is wired for internet, one is wireless for intranet.

I maybe know hwo to setup router and NAT, but have no idea hwo to set my intel wireless card to master mode(managed and ad-hoc mode work fine).

I really appreciate any suggestions.

---

