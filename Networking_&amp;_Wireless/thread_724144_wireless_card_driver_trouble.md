---
title: "wireless card driver trouble"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by GreTTin on 2008-03-14
Hi all,

I've insalled xubuntu on a laptop and am trying to get the wireless card to work.
I've tried both the madwifi way and the ndiswrapper way (or atleast think I have) to no avail.

the wireless card is by ```
vendor: Atheros Communications, Inc.
```

and is model number ```
product: AR2413 802.11bg NIC
```

I can see the wireless network with ```
clair@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Gary's WLAN"  Nickname:"Gary's WLAN"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:07:18:64   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-33 dBm  Noise level=-90 dBm
          Rx invalid nwid:6  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

but cannot for the life of me connect to it. Any help will be greatly appreciated.
If you would like more information don't hesitate to ask.

Thankyou in advance.

---

### Post by mrsteveman1 on 2008-03-14
Technically you are connected to it, but that doesn't mean the AP has authorized you, only that you are associated with the AP at the moment.

Is this a WPA2 network? If not, have you run dhclient on the interface to get an IP?

---

### Post by GreTTin on 2008-03-14
yes this is wpa, i would rather use this as this is the most secure. do you think I should try wep? 

dhclient gives me an odd output ```
clair@laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5767
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/ath0/00:12:bf:65:10:56
Sending on   LPF/ath0/00:12:bf:65:10:56
Listening on LPF/eth0/08:00:46:90:92:37
Sending on   LPF/eth0/08:00:46:90:92:37
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.6 -- renewal in 941975458 seconds.
```

eth0 being the wired connectio i'm writing on here.

---

### Post by GreTTin on 2008-03-14
Just tried wep and unsecured and cannot connect like that either.

Seems like I can't get an ip address off the router?
maybe i'm not tx?

Any ideas?

---

### Post by GreTTin on 2008-03-14
ok got unencrypted working by removing ndiswrapper and all the gui's for setting up wireless.

Followed the sticky on setting up wpa and had it fail on bringing it back up :(

Any one got any advice?

---

### Post by GreTTin on 2008-03-14
can only get unencrypted to work if i set it up with iwconfig, can't use /etc/network/interfaces as then it will not work. any ideas?

---

### Post by mrsteveman1 on 2008-03-14
I would stick with madwifi, since if your chipset is supported, it is in theory a better driver with support from Atheros.

Does network manager not work at all?

---

### Post by GreTTin on 2008-03-15
hey, thanks for the reply.

network manager (assuming this is the same as network in xubuntu) sees the connection when i click on the essid drop down menu, but when i click on it it says it's changing network. when that ends it is still not connected and says ip none in the corner.

---

