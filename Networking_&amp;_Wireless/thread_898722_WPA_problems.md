---
title: "WPA problems"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by longboneslinger on 2008-08-23
Ok, more networking fun. I'm trying to set up my router for added security using WPA1 personal. I'm currently using the SES (Secure Easy Setup) generated passkey which is to short for my tastes.
I went to my my Linksys routers page 192.168.1.1 and logged in. I went to Wireless-->Wireless Security and set:
Security Mode: WPA Personal
WPA Algorithms: AES
WPA Shared  Key: <random 63 bit ASCII>
Group Key Renewal: 3600 (Default)

I'm using Ubuntu Hardy with wicd and madwifi. I set WICD:
Checked use encryption
WPA1/2
Key <random 63 bit ASCII> used in router setup.

No connection for my Acer lappy. I was connecting fine using the SES generated key. I just put in the SES passkey before, it apparently converts it automatically, but WICD wouldn't take it as 63 bit. It greyed out for a minute or so, tried to connect for a few minutes and failed.   I then used this code to generate a passkey for WICD:
```
wpa_passphrase <my_SSID> <63 bit ASCII>
```
Here's the code output:
```
bash: !t: event not found
```

I switched to wifi-radar to see if it was wicd but no dice. I ran it at the command line so I could see what was wrong. Since I have no idea I'll post it here. I warn you though, it's long:
```
sudo wifi-radar
dhclient3 --version 2>&1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "MY SES passkey".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
Stale pid file.  Removing
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 37932 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 2397
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
sh: Syntax error: ")" unexpected
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Stale pid file.  Removing
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "MY SES passkey".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Stale pid file.  Removing
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "MY SES passkey".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:38:63:36:f8
Sending on   LPF/eth0/00:1b:38:63:36:f8
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Stale pid file.  Removing
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_supplicant.conf'.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1d:d9:4b:36:0e
Sending on   LPF/ath0/00:1d:d9:4b:36:0e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 34532 seconds.



```


For now I'm gonna put it back to the original SES generated key mainly to keep wifeys lappy on the net. Since I married the stereo-typical redhead this is a must. 
Everyone keeps talking about "Getting to the top if the learning curve.". I'm still trying to find the bottom. The more I learn, the more I realize I'm clueless. Sigh. If I can get this straightened out I'll try to figure out how to set up static IPs with mac filtering but that's another day and another thread. 
Later taters,
bone

Edit/addition-I rebooted the comp to see if it would help. I had no internet. None.  I tried to ping google but got unknown host. So I popped a ethernet cord into the lapy from the router and still no 'net. ifconfig showed eth0 as 'no wireless extensions'. I rebooted again with no luck. Even hardwired in I had nothing. Ooookkkkk.....I opened synaptic and removed wifi-radar and re-installed wicd and bingo. The net is back.Rebooted the lapy and the net is still available. Cool. Now if I can convince wicd to automatically connect on startup. I have the 'automatically connect' box checked but it doesn't. Oh well, that's minor. I don't know if this is useful info but I thought I'd toss it in. Why can't I have normal problems? Sigh, Like my life isn't interesting enough as it is. It's a good thing I like to learn or I'd go nuts.

---

