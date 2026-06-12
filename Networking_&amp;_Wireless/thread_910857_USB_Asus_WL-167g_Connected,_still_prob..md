---
title: "USB Asus WL-167g Connected, still prob."
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by mavreix on 2008-09-04
So my card works right out of the box with a fresh ubuntu install.  The only thing is that when I connect to my WPA network there is no actual connection.  Let me post some script

This is after a dmesg

```

not in authenticate state - ignored 
[  778.226958] wlan0: Initial auth_alg=0 
[  778.226970] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  778.264445] wlan0: association frame received from 00:1c:10:8d:47:89, but not in associate state - ignored 
[  778.316851] wlan0: RX authentication from 00:1c:10:8d:47:89 (alg=0 transaction=2 status=0) 
[  778.316859] wlan0: authenticated 
[  778.316864] wlan0: associate with AP 00:1c:10:8d:47:89 
[  778.340423] wlan0: RX ReassocResp from 00:1c:10:8d:47:89 (capab=0x411 status=0 aid=3) 
[  778.340441] wlan0: associated 
[  778.340508] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0 
[  778.340512] wlan0: failed to set TX queue parameters for queue 2 
[  778.340515] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0 
[  778.340517] wlan0: failed to set TX queue parameters for queue 3 
[  778.340521] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30 
[  778.340524] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15 
[  786.358416] wlan0: RX deauthentication from 00:1c:10:8d:47:89 (reason=15) 
[  786.358423] wlan0: deauthenticated 
[  787.354681] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  787.554236] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  787.732620] wlan0: RX deauthentication from 00:1c:10:8d:47:89 (reason=7) 
[  788.727573] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  788.927104] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  789.126643] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  789.326183] wlan0: authentication with AP 00:1c:10:8d:47:89 timed out 
[  790.174848] wlan0: Initial auth_alg=0 
[  790.174860] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  790.186358] wlan0: Initial auth_alg=0 
[  790.186370] wlan0: authenticate with AP 00:1c:10:8d:47:89 
[  790.191166] wlan0: RX authentication from 00:1c:10:8d:47:89 (alg=0 transaction=2 status=0) 
[  790.191175] wlan0: authenticated 
[  790.191179] wlan0: associate with AP 00:1c:10:8d:47:89 
[  790.192412] wlan0: authentication frame received from 00:1c:10:8d:47:89, but not in authenticate state - ignored 
[  790.192996] wlan0: authentication frame received from 00:1c:10:8d:47:89, but not in authenticate state - ignored 
[  790.195055] wlan0: authentication frame received from 00:1c:10:8d:47:89, but not in authenticate state - ignored 
[  790.197699] wlan0: RX ReassocResp fr

```

This is after a network reset
```

wlan0     IEEE 802.11g  ESSID:"WildBoys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:8D:47:89   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/100  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

 Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 12047 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:13:d4:4b:0a:b4 
Sending on   LPF/wlan0/00:13:d4:4b:0a:b4 
Sending on   Socket/fallback 
DHCPRELEASE on wlan0 to 192.168.0.1 port 67 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:13:d4:4b:0a:b4 
Sending on   LPF/wlan0/00:13:d4:4b:0a:b4 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

```

I dont understand what is going on Ive tried to manually configure the connection but it still gets the same message.  
Any help would be appreciated.

---

### Post by mavreix on 2008-09-05
Bump.

---

