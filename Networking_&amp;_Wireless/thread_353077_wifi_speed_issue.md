---
title: "wifi speed issue"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by casaschi on 2007-02-04
My wifi connection from Ubuntu to the DSL router is sort of "working", but I have a connection speed issue; I wonder if anyone had a similar situation and how they solved it.

My setup is with a Linksys PCMCIA card (WPC54Gv5) and DSL router WAG354G, so I should get a full 802.11G connection at 54Mbps.

The laptop on Ubuntu is using ndiswrapper and wifi-radar (cant use network-manager because it fails to properly authenticate with wpa_supplicant, wifi-radar connects fine).

I kept the laptop in the same room as the router for the whole of the testing.
When the connection starts, iwconfig on the card reports a connection at 36Mbps, or 18Mbps. As soon as I start sending some continuous data (e.g. copying a file from another machine), the connection drops at 11Mbps and sticks there.

Another laptop (with onboard Intel WiFi) had a steady connection at 54Mbps, so there must be something wrong either with the laptop card or the sw config.

I tried asking the Linksys forum and I got few suggestions
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=4131](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=4131)
Essentially they suggested changing some parameters on the router (changing the channel to 6, 9 or 11. Reduce the beacon interval to 50 and RTS and Fragmentation threshold by 40 each...) but I had no improvement.

This is my "iwconfig wlan0" output:
```

wlan0     IEEE 802.11g  ESSID:"whatever"  Nickname:"whatever"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:11:22:33:44:55   
          Bit Rate=11 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-70 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Tried to mirror the settings changes on the card, but again no improvements.

Anyone any suggestion before I give up (and shop for another card if I want full 54Mbps)???

Thanks!

---

### Post by tturrisi on 2007-02-04
You'll never get a full 54mbps on any wifi card.  There are bottlenecks here & there that prevent it, such as MTU setting, driver code, AP configs, AP performance, AP-router firmware code, AP wlan device driver code (the AP itself has an internal wifi card-device), channel, interference from other devices/microvaves, IP version used, comp configs, other related hardware, etc, etc, etc.  Exactly WHY the card does not perform better could be one, some or all of the above!

---

### Post by casaschi on 2007-02-04
Thanks for the optimistic reply tturrisi! :-)

But then, there is a big gap between the theoretical 54Mbps and the actual 11Mbps.
Also, how would you explain that my work laptop with onboard Intel wireless (and winxp) is getting a steady 54Mbps from the same access point???

The bottom line is that with the winlaptop I can watch video direclty from my small home NAS, with the linux laptop I have to copy the files first otherwise the playback across the network breaks often. Addressing this is the goal of my question...

---

### Post by tturrisi on 2007-02-04
The windows drivers are entirely different than the linux drivers, even if use ndis-wrapper & win drivers on linux.  Linux use the wifitools, which are less than perfect and all linux wifi is nowhere near the quality of windows wifi.  It just a fact, that's all.  Not dissing linux or windows, just stating the obvious.

I'm 6' away from my AP and this is my result:
```
ath0      IEEE 802.11g  ESSID:"8724"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:9F:DD:04
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx  Security mode:restricted
          Power Management:off
          Link Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:
```

Your wpc546v5 has a Broadcom chipset.  These chipsets do not perform well in linux using the bcm43xx driver (if can get it working at all w/ that driver!) and they perform semi-ok using win driver w/ ndiswrapper.  I would wager that using a different chipset card such as one with acx or atheros will solve the issues.  Broadcom wifi chipsets are THE most problematic devices of them all.  For proof, do a forum search here for broadcom and notice all the disappointment.

---

### Post by casaschi on 2007-02-04
Actually, I have a Marvell chip, that apparently is even worse than Broadcom as far as native driver availability. Not really an issue for me to use ndiswrapper, if only I could get a slightly better speed to allow streaming from the file server.

lspci tells me:
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

This is the ndiswrapper .conf file for the driver, but I have no clue if any of the settings should be changed to improve the speed...

 
```

NdisVersion|0x50001
Environment|1
BusType|5
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Linksys,10/13/2004,3.1.0.36

AdhocGMode|0
DriverRel|10/13/2004
FragThsd|2306
LED0Associated|ff0005
LED0Joined|ff0006
LED0PowerOff|fe0000
LED0PowerOn|30001
LED0Rx|ff0009
LED0RxHigh|ff000d
LED0Scan|ff0002
LED0Started|ff0007
LED0Tx|ff0008
LED0TxHigh|ff000c
LED1Associated|fe0105
LED1Joined|ff0106
LED1PowerOff|fe0000
LED1PowerOn|fe0101
LED1Rx|30109
LED1RxHigh|2010d
LED1Scan|40102
LED1Started|ff0107
LED1Tx|30108
LED1TxHigh|2010c
PowerMode|0
Preamble|1
RTSThsd|2307
TxWepKey|
WepKey1|
WepKey2|
WepKey3|
WepKey4|

```

---

### Post by tturrisi on 2007-02-05
try this to get current rate:

$# sudo /sbin/iwlist ath0 rate|grep Current
(change ath0 to your interface)

---

