---
title: "Wireless / No internet..."
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by kevaljd on 2008-08-06
Hey there...

something funny happened... am new to ubuntu but did work with fedora...
I somehow got my wireless Driver installed! thanks to madwifi

I can see the list of wireless networks available in the range but I cannot connect to internet... Funny thing is, whtever i put wep or wpa1 key, it shows its connected! to any network... even if i click on cancel...

I went thru settings and enable roaming mode... fortunately my wired started working so am here!!! My laptop isnt getting any ip address, its auto - dhcp...

I tried running dhcp as a sudo and thought it would work... I got the following output:

~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 8098
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1c:26:36:0f:6f
Sending on   LPF/ath0/00:1c:26:36:0f:6f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I tried modprobe ath_pci
I also tried sudo ifconfig ath0 up

no go...
It can detect wireless networks but doesnt get an IP address...
pls reply thanks
thanks!

---

### Post by pytheas22 on 2008-08-06
It sounds like a problem with Network Manager.  You could try using [wicd]("http://wicd.sourceforge.net") instead.

If that doesn't help, please post the output of:
```

lspci -nn
lsusb
lshw -C Network
iwlist scan
```

---

### Post by kevaljd on 2008-08-07
Yes issue was with Network manager... I just tried to re-configure everything and its working.

Thanks anyways...
Take care and pls close this thread.

---

