---
title: "Wireless Connection almost configured still not working"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by boilermaker on 2007-01-07
Hi Folks:

I have been trying my best to make the wireless connection work and here is what i have so far. 


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

$  ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 


$ sudo gedit /etc/modprobe.d/blacklist

blacklist bcm43xx

[B][COLOR="Red"]This removes the wireless connection from the System->Administration->Networking Window
[/COLOR][/B]


$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

$ sudo ifdown wlan0

ifdown: interface wlan0 not configured

[COLOR="Red"]**Can someone tell me how this could be changed! I mean how could i make it recognize wlan0**[/COLOR]

$ sudo iwconfig wlan0
wlan0     IEEE 802.11b/g  ESSID:"1L886"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:0FB2-9CA1-75   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ sudo iwlist wlan0 scanning
wlan0     Interface doesn't support scanning : No such device


$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/wlan0/00:14:a5:83:48:e9
Sending on   LPF/wlan0/00:14:a5:83:48:e9
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down


sudo gedit /etc/modules

[COLOR="Red"]**The file contains lp apart from ndiswrapper I am not sure if that is how it is mean to be!**[/COLOR]



sudo gedit /etc/network/interfaces



auto wlan0
iface wlan0 inet static
wireless-essid 1L886
wireless-key 0FB29CA175
address 192.168.1.190
netmask 255.255.255.0
gateway 192.168.1.1


#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


[COLOR="Red"][B]Is this correct????
[/B][/COLOR]



$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting System Tools Backends system-tools-backends                  [ ok ] 



$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/wlan0/00:14:a5:82:78:e9
Sending on   LPF/wlan0/00:14:a5:82:78:e9
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down



[COLOR="Red"][B]
What is SIOCSIFFLAGS??[/B][/COLOR]

Result:
When i reboot the computer i have the wireless connection showing up as not connected and the signal meter is low yellow!


Thanks in advance

---

