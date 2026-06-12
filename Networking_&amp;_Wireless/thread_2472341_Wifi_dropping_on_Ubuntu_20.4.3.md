---
title: "Wifi dropping on Ubuntu 20.4.3"
date: 2022-02-24
forum: Networking &amp; Wireless
---

### Post by mamlfcosta on 2022-02-24
For the past couple days my WiFi has been dropping on my laptop, every few seconds for some unknown reason, gathered the following information below(redacted MAC addresses) to see if anyone would provide some help on troubleshooting the issue which has become quite annoying.

~$ dmesg -w | grep wlp0s20f3


[78106.935166] wlp0s20f3: disconnect from AP xx:xx:xx:xx:xx:xx for new auth to xx:xx:xx:xx:xx:xx
[78106.964453] wlp0s20f3: authenticate with xx:xx:xx:xx:xx:xx
[78106.964485] wlp0s20f3: AP VHT information is invalid, disable VHT
[78106.964491] wlp0s20f3: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[78106.967524] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[78107.096962] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 2/3)
[78107.198327] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 3/3)
[78107.479005] wlp0s20f3: authentication with xx:xx:xx:xx:xx:xx timed out
[78108.716480] wlp0s20f3: authenticate with xx:xx:xx:xx:xx:xx
[78108.721576] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[78108.850721] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 2/3)
[78108.852390] wlp0s20f3: authenticated
[78108.854751] wlp0s20f3: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[78108.857146] wlp0s20f3: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x1511 status=0 aid=1)
[78108.861854] wlp0s20f3: associated
[78111.616078] wlp0s20f3: disconnect from AP xx:xx:xx:xx:xx:xx for new auth to xx:xx:xx:xx:xx:xx
[78111.641156] wlp0s20f3: authenticate with xx:xx:xx:xx:xx:xx
[78111.641179] wlp0s20f3: AP VHT information is invalid, disable VHT
[78111.641182] wlp0s20f3: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[78111.644531] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[78111.770878] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 2/3)
[78111.872077] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 3/3)
[78112.158251] wlp0s20f3: authentication with xx:xx:xx:xx:xx:xx timed out
[78112.421817] wlp0s20f3: authenticate with xx:xx:xx:xx:xx:xx
[78112.427315] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[78112.554902] wlp0s20f3: send auth to xx:xx:xx:xx:xx:xx (try 2/3)
[78112.556608] wlp0s20f3: authenticated
[78112.558819] wlp0s20f3: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[78112.561487] wlp0s20f3: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x1511 status=0 aid=1)
[78112.566306] wlp0s20f3: associated


~$ nmcli general
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled


~$ nmcli dev wifi list
IN-USE  BSSID              SSID                        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY         
        xx:xx:xx:xx:xx:xx  DIRECT-5f-HP M283 LaserJet  Infra  8     130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  5     130 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  8     130 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  8     130 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  5     130 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2             
*       XX:XX:XX:XX:XX:XX  Neowise                     Infra  48    270 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  2     130 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  2     130 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  116   270 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  48    270 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  5     130 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2        
        XX:XX:XX:XX:XX:XX  BTWi-fi                     Infra  11    195 Mbit/s  54      &#9602;&#9604;__  --               
        XX:XX:XX:XX:XX:XX  J.A.R.V.I.S.                Infra  11    195 Mbit/s  52      &#9602;&#9604;__  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  11    195 Mbit/s  52      &#9602;&#9604;__  WPA2             
        XX:XX:XX:XX:XX:XX  J.A.R.V.I.S.                Infra  36    540 Mbit/s  32      &#9602;&#9604;__  WPA2             
        XX:XX:XX:XX:XX:XX  --                          Infra  36    540 Mbit/s  32      &#9602;&#9604;__  WPA2             
        XX:XX:XX:XX:XX:XX  BTWi-fi                     Infra  36    540 Mbit/s  30      &#9602;___  --               
        XX:XX:XX:XX:XX:XX  BTWifi-X                    Infra  36    540 Mbit/s  29      &#9602;___  WPA1 WPA2 802.1X 
        XX:XX:XX:XX:XX:XX  SurroundMaster_c2fe88       Infra  52    65 Mbit/s   29      &#9602;___  WPA2             
        XX:XX:XX:XX:XX:XX  Neowise                     Infra  116   270 Mbit/s  0       ____  WPA2
        
~$ nmcli dev status
DEVICE             TYPE      STATE         CONNECTION 
wlp0s20f3          wifi      connected     Neowise    
docker0            bridge    connected     docker0    
ppp0               ppp       disconnected  --         
p2p-dev-wlp0s20f3  wifi-p2p  disconnected  --         
enp0s31f6          ethernet  unavailable   --         
enx747827ee4291    ethernet  unavailable   --         
lo                 loopback  unmanaged     --



~$ sudo iwconfig wlp0s20f3
 
wlp0s20f3  IEEE 802.11  ESSID:"Neowise"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=780 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46   Missed beacon:0

---

### Post by TheFu on 2022-02-24
For 2.4Ghz, there are only 3 channels that don't overlap.  1, 6, 11. Using others should be avoided.  
Turn off all the other wifi devices and anything that is working on both 2.4Ghz and 5.8Ghz. Get the minimal interference that you can.  That includes wireless DECT desk phones and handsets, all bluetooth stuff, and see if that helps.

If would be really good if you posted the actually wifi device used and drivers.
There are about 50 different settings for most wifi clients that can drastically impact performance. Some are there because wifi devices are mobile and how quickly a client switches between different APs can be tuned. If your device is halfway between 2 different devices, it can end up switching back and forth, which will destroy real throughput.

Almost always, recommendations will be tied to a specific wifi chip version, driver version and AP. Please provide those.

Or plug in an ethernet port.

---

