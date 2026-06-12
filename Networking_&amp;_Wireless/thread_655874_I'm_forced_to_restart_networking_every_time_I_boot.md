---
title: "I'm forced to restart networking every time I boot"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by Lido on 2008-01-01
I just installed Mythbuntu and every time I boot the machine, networking won't work. I then do: ```
sudo /etc/init.d/networking restart
``` and it starts working. Here's my ifconfig after boot (i.e. NOT working):```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:30:67:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:D1:69:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-D1-69-D1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
Here it is after restart:```
$ sudo /etc/init.d/networking restart
[sudo] password for lido:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 5744
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
run-parts: run-parts: component /etc/network/if-post-down.d/avahi-daemon is a broken symbolic link

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 2147483648 seconds.
                                                                         [ OK ]
```

---

### Post by Lido on 2008-01-02
Anyone?

---

### Post by santosh_gr on 2008-01-02
what does your /etc/network/interfaces look like?

---

### Post by Lido on 2008-01-03
```
$ more /etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk [long key here]
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Linksys

auto wlan0
```

---

### Post by santosh_gr on 2008-01-03
The auto-wlan0 should come earlier in the file, like shown below.  After you make this change restart networking using the command "sudo /etc/init.d/networking restart" without quotes.

-----------------------------------------------------------------------------
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk [long key here]
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Linksys

---

### Post by WhyWontThisWork on 2008-01-04
when i did mine i installed ndiswrapper from command line and then just finalized the install and it all works fine.....

---

### Post by lusis89 on 2008-01-04
> **santosh_gr said:**
> The auto-wlan0 should come earlier in the file, like shown below.  After you make this change restart networking using the command "sudo /etc/init.d/networking restart" without quotes.

-----------------------------------------------------------------------------
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-psk [long key here]
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Linksys

that doesn't matter :lolflag:

---

### Post by lusis89 on 2008-01-04
> **Lido said:**
> Anyone?

Try this after boot when network is not working
```
ifconfig wlan0 down
ifconfig wlan0 up
iwconfig wlan0 mode Managed
iwconfig wlan0 essid [your essid]
iwpriv wlan0 set NetworkType=Infra
iwpriv wlan0 set AuthMode=WPA2PSK
iwpriv wlan0 set EncrypType=AES
iwpriv wlan0 set WPAPSK=[your key]
dhclient wlan0

```

if it does work save the file attached to this post in /etc/init.d/
and follow 1 or 2.

**1)**
from a terminal do:
```
sudo ln -sv /etc/init.d/wireless-start.sh /etc/rc3.d/S99wireless-start
```

**2)**
Install serviceconfig
```
sudo apt-get install sysvconfig
```

run serviceconfig as root
```
sudo serviceconfig
```
(e.g. from a terminal)

set Run Level to "Multi-user (3)"
and in the list search "wireless-start" and check the box at the right, then Close.

---

### Post by Lido on 2008-01-05
Santosh, I tried moving the auto wlan0 up in my file, but it's still not coming up when I boot. The device I'm using is an Edimax USB wireless adapter. I don't know if that makes a difference. In dmesg I see the following:```
ieee80211_init: failed to initialize WME (err=-17)
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
wmaster0: Selected rate control algorithm 'simple'
```

Which is discussed at length here with no clear resolution:
[https://bugs.launchpad.net/ubuntu/+bug/144239](https://bugs.launchpad.net/ubuntu/+bug/144239)

Even when I change my wireless setup to static, I still have the problem (won't work until I restart networking).

When I restart networking, I also get this (troubling parts in red):
```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                             There is already a pid file /var/run/dhclient.wlan0.pid with pid 5643
killed old client process, removed PID file
...
[COLOR="Red"]wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
[/COLOR]Listening on LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
[COLOR="Red"]send_packet: please consult README file regarding broadcast address.
run-parts: run-parts: component /etc/network/if-post-down.d/avahi-daemon is a broken symbolic link

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 0[/COLOR]
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   LPF/wlan0/00:0e:2e:d1:69:d1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 2147483648 seconds.
```

Lusis, Thanks for the response. I can't get the "iwpriv wlan0 set" commands to work:```
$ iwpriv wlan0 set NetworkType=Infra
Invalid command : set
```
...and if you're suggesting adding a shell script to init, why not just:
```
/etc/init.d/networking restart
```
?

---

### Post by sdide on 2008-01-05
It seems the network is trying to initialize before the wireless things are ready.

Its not a solution, merely a workaround, but you could try
adding the line /etc/init.d/networking restat
in the /etc/rc.local file.

---

### Post by Lido on 2008-01-06
Sdide,
Thanks, yes, that's what I was suggesting in the last line of my previous post. I don't like that solution, but I prefer it to installing something else (like ndisdwrapper), and so that's what I'm doing for now. At least my mom still thinks I'm smart.

---

