---
title: "mac80211_hwsim monitor mode"
date: 2017-05-09
forum: Networking &amp; Wireless
---

### Post by hy+ on 2017-05-09
Hello,

I am trying to use mac80211_hwsim in monitor mode, but when I transmit an 802.11 frame on one simulated interface it does not appear on another simulated interface.

I have the hwsim module loaded with the default two interfaces (wlan0 and wlan1):

```
y@tower:~$ lsmod | grep hwsim
mac80211_hwsim         45056  0 
mac80211              733184  2 ath9k_htc,mac80211_hwsim
cfg80211              561152  5 ath,ath9k_common,mac80211,ath9k_htc,mac80211_hwsim

y@tower:~$ iwconfig 
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11abgn  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

I set the monitor mode on each interface and the channel as follows:

```
ip link set dev wlan0 down
iw dev wlan0 set type monitor
ip link set dev wlan0 up
iw dev wlan0 set channel 1

ip link set dev wlan1 down
iwconfig wlan1 mode monitor
ip link set dev wlan1 up
iw dev wlan1 set channel 1
```

And then I transmit a frame using the following python script:

```
from scapy.all import *
 
class Dot11EltRates(Packet):
    """ Our own definition for the supported rates field """
    name = "802.11 Rates Information Element"
    # Our Test STA supports the rates 6, 9, 12, 18, 24, 36, 48 and 54 Mbps
    supported_rates = [0x0c, 0x12, 0x18, 0x24, 0x30, 0x48, 0x60, 0x6c]
    fields_desc = [ByteField("ID", 1), ByteField("len", len(supported_rates))]
    for index, rate in enumerate(supported_rates):
        fields_desc.append(ByteField("supported_rate{0}".format(index + 1),
                                     rate))
 
packet = Dot11(
    addr1="00:a0:57:98:76:54",
    addr2="00:a0:57:12:34:56",
    addr3="00:a0:57:98:76:54") / Dot11AssoReq(
        cap=0x1100, listen_interval=0x00a) / Dot11Elt(
            ID=0, info="MY_BSSID")
packet /= Dot11EltRates()
sendp(packet, iface="wlan0")
```

I am able to see the transmitted frames with Wireshark on wlan0, but nothing appears on wlan1. From the description of the mac80211_hwsim I would think that frames transmitted on channel 1 via wlan0 should be copied to wlan1 receive queue, since it is on the same channel.

Does anyone know what the problem might be?

Thank you.

---

### Post by chris-stone on 2018-01-01
Hi, did you ever figure out a solution to this? I am trying to do the same thing. 

Thanks

---

### Post by sdegree on 2018-01-13
you just need hostapd and wpa_supplicant to set the connection first

---

