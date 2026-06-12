---
title: "ndiswrapper - Can't configure network"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Xikkub on 2008-11-16
I finally fixed my ndiswrapper installation and got it to recognize my wireless usb adapter. Now I need to configure the network for my SSID and for WPA.

When I click the "Configure Network" at the System->Administration->Windows Wireless Drivers, nothing happens.

When I look at my "Network Connections", I find myself completely clueless how to configure my Wireless there.

So how and where would I enter my network settings? 
Thanks!

----------

#iwlist scanning
```
lo       Interface doesn't support scanning.
eth0     Interface doesn't support scanning.
wlan4    No scan results
pan0     Interface doesn't support scanning.
```

#iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan4     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

