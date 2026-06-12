---
title: "wireless internet goes out shortly after booting"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by backflop on 2007-03-11
Hi, 

[INDENT][/INDENT]I've been using Ubuntu for a couple of months now, and recently had to start using a wireless connection. I am using a Hawking HWP54G based on the Texas Instruments' ACX 111 and am not using the ndiswrapper because I have connected to the internet through my adapter without using it. When I boot to Ubuntu, I can browse the internet without any network managers like kwifi manager or wireless lan assistant opened, but after five minutes or so I can't browse the internet and get the Firefox Cannot Locate Server message. So i've tried using the network managers listed above, but the same thing happens, and when I check Kwifi Manager it gives me an ESSID, an access point, an IP address, and a signal strength. 

While I have access to the internet my iwconfig output is this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"2WIRE065"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E4:DE:53:21   
          Bit Rate:6 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=38/100  Signal level=13/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

When I don't have access to the internet my iwconfig output is this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"2WIRE065"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E4:DE:53:21   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=40/100  Signal level=16/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

sit0      no wireless extensions.
```

I am using Edgy, and new to using wireless networks. I am using DHCP. Any help is appreciated and I know that the router and modem work well because there are computers running XP that have stable connections.

---

### Post by backflop on 2007-03-13
Not sure why it went out in the first place considering the almost identical outputs, but everything is working fine now.

---

