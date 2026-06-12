---
title: "madwifi DWL-AG530 ioctl: operation not permitted"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by oddmind on 2007-06-01
***THIS HAS BEEN SOLVED***
thank you tturrisi


well im running 6.10 and i think im real close to getting this to work. Ive got a D-link DWL-AG530 and followed this guide

[http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi)

when i tried to do this...

```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

after sudo modprobe ath_pci

i get this error

"wlanconfig: ioctl: Operation not permitted"

and then ifconfig gives me this }(im using ethernet to install madwifi)


ath0      Link encap:Ethernet  HWaddr 00:11:95:8B:AB:88  
          inet6 addr: fe80::211:95ff:fe8b:ab88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:19:DB:2D:35:70  
          inet addr:192.168.15.104  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe2d:3570/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25496948 (24.3 MiB)  TX bytes:1198306 (1.1 MiB)
          Interrupt:233 Base address:0xf200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-8B-AB-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11216 errors:0 dropped:0 overruns:0 frame:979
          TX packets:80266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:665875 (650.2 KiB)  TX bytes:3933034 (3.7 MiB)
          Interrupt:50 


if anyone could help me out that would be great

---

### Post by tturrisi on 2007-06-02
That's an old madwif install guide.
Do this and get the latest madwifi along with a patch to allow madwifi to work w/ aircrack.  (note, you need not ever use aircrack but this is an easy install.

```
Uninstall the linux-restricted-modules madwif first. else you will get build errors.
This should also prompt to uninstall any existing madwifi drivers.
Open a root terminal.

apt-get install build-essential 
apt-get install linux-headers-$(uname -r)
apt-get install subversion
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```

---

### Post by oddmind on 2007-06-02
wow thanks, i've completed the install... now should my wireless card just work?

Is there anything else I need to type or setup?

---

### Post by oddmind on 2007-06-02
wow thanks, i've completed the install... now should my wireless card just work?

Is there anything else I need to type or setup?

ok its still not working, im sorry but im very new to this. I don't know what to do next. I restarted the network like it says in the old guide, this is what I get.
```


# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         There is already a pid file /var/run/dhclient.eth0.pid with pid 4108
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:19:db:2d:35:70
Sending on   LPF/eth0/00:19:db:2d:35:70
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.15.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 4744
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:8b:ab:88
Sending on   LPF/ath0/00:11:95:8b:ab:88
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:8b:ab:88
Sending on   LPF/ath0/00:11:95:8b:ab:88
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:19:db:2d:35:70
Sending on   LPF/eth0/00:19:db:2d:35:70
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                        [ ok ]

```

wireless connection is recognized in system-administration-networking

Could someone help me with the next steps? Is there anything you need to know first?

---

### Post by tturrisi on 2007-06-02
It's working!
You just sre not connected to the access point.
If your wlan does not use security (wep or wpa) then put this in your /etc/network/interfaces file.  Do:

sudo gedit /etc/network/interfaces
```
iface ath0 inet dhcp
wireless-essid TYPE_YOUR_SSID_HERE
#wireless-key XXXXXXXXXX  #(if use wep then remove first # & replace the x's w/ your wep key)
auto ath0
```
reboot

---

### Post by oddmind on 2007-06-02
wow!

It's finally working :D

Thank you so much! I''m submitting this through a wireless connection on Ubuntu :]

---

### Post by tturrisi on 2007-06-02
very well done!

---

