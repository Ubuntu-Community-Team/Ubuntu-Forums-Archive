---
title: "Cannot connect AP wit WUSB54Gv4 (UbuntuStudio x89_64)"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Yamigami on 2007-11-18
Hello,

I have recently downloaded and installed UbuntuStudio(2.6.22-14-rt) for my AMD64 everything went nearly smooth until I wanted to connect the internet using my Linksys WUSB54Gv4. I searched the forums for possible driver solution and found out that serialmonkey'  (rt73 excatly) driver worked for most people. I managed to compile and install the driver and started my wireless device even I managed to configure and associate it with my access point which uses WEP encryption I couldn't connect it. Also I am gettting very weak signals froms my AP. This is the last situation in my case :) 

[IMG]http://farm3.static.flickr.com/2062/2042754725_68f5bac826.jpg?v=0[/IMG]

This my iwlist scan results.

```

alper@studio:/etc$ sudo iwlist wlan0  scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:28:50:61
                    ESSID:"TerminalReality"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-41 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000001a93c9667

```


iwconfig for wlan0

```

alper@studio:/etc$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"TerminalReality"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:28:50:61   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:E3DF-C301-35
          Link Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Crappy no response stuff.

```
alper@studio:/etc$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8309
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:a4:0b:fb
Sending on   LPF/wlan0/00:12:17:a4:0b:fb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

:(

Any alternative solutions are welcome. Thanks

---

