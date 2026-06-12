---
title: "Wireless driver installed but cannot make connection"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-09-10
I'm using a new MacBook (C2D, Atheros 5212 wireless card) with Ubuntu as one of various OSes.
Wireless works perfectly on Mac OSX but is really causing me some grief in Ubuntu.
Strange thing is that I did have it working about a week ago without problem but now I can't get it back.
I believe the driver (madwifi) is properly installed but for some reason I can't get a "DHCPOffer".
Not sure what to do next so would appreciate some/any advice.
Here's what I've done up to now:

1) Created and installed madwifi driver. When I run "iwconfig" I get
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:240798  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
which I believe verifies that the driver is successfully loaded.

2) Use
```
sudo ifconfig ath0 up
```
to bring up wireless interface

3)Scanned for AP with
```
sudo iwlist ath0 scan
```
and get
```

ath0      Scan completed :
          Cell 01 - Address: 00:0F:CC:23:B6:0C
                    ESSID:"eircom1073 4700"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=78/70  Signal level=-17 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

```
telling me an AP is available.

4) I connected to AP using
```
 sudo iwconfig ath0 ap 00:0F:CC:23:B6:0C
```

5) Then I used the WEP key to complete the connection
```
sudo iwconfig ath0 key <wep key (in hex)>
```

6)Finally I tried 
```
sudo dhclient ath0
```
but only get the following despite multitudinous attempts.
```
  There is already a pid file /var/run/dhclient.pid with pid 20620
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1c:b3:b4:9e:98
Sending on   LPF/ath0/00:1c:b3:b4:9e:98
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Can anybody please tell me what might be going wrong here?

Thanks
Paul

---

### Post by jnorthr on 2007-09-10
Have you made any changes to the ap like adding wep security or some such ? I'd see if turning off the wep on both sides might help at least get re-established. Your output looks like mine.

The big number of rx invalid nwid bothers me but that's just a feeling - dunno why ...

---

### Post by PaulFXH on 2007-09-10
No, I have not (conciously anyway) made any changes to the AP.
It does, however, already have a WEP key which i always use.
However, less than two weeks ago I was able to wirelessly connect (including the WEP key) without any problems.
I might try tomorrow to take out the WEP security just to see will it work without it.

---

