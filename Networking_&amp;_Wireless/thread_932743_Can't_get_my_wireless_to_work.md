---
title: "Can't get my wireless to work"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by MrDiaz on 2008-09-28
My laptop is a Sony Vaio FW-160, I've installed the drivers already. Here's what I get from iwconfig.

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I then follow directions in the sticky above and 

```

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:e2:ca:55:b0
Sending on   LPF/wlan0/00:1f:e2:ca:55:b0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I disable the wired network, try to connect to "enemy" (my wireless ssid) it'll pop the window open to type my WEP key, I type but nothing happens. Keeps loading forever. I disabled the network protection just in case it was a WEP issue, I try to connect again to enemy but it just keeps loading, nothing happens. 

If you guys can help that'd be great!

---

### Post by MrDiaz on 2008-09-29
bump

---

### Post by melojo on 2008-09-29
Have a look here.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
what do you get when you type
iwlist scan in a terminal

---

