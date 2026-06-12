---
title: "One wifi-card, two interfaces"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by plebeien on 2005-11-03
I got a problem with my new T40 and breezy since the beginning. There's inside a cisco aironet 802.11b wifi card. this card is recognized by the system (listed in device manager as eth0) lsmod and lspci shows that everything is ok.
but when I want to configure it in the network part, I got two interfaces linked to the wifi card : eth0 and eth3,  eth1 being my lan interface.
if I do a iwconfig, I got this :

eth0      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: FF:FF:FF:FF:FF:FF   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-107 dBm  Noise level=-107 dBm
          Rx invalid nwid:2078  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4682   Missed beacon:0

eth3      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: FF:FF:FF:FF:FF:FF   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-107 dBm  Noise level=-107 dBm
          Rx invalid nwid:2078  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4682   Missed beacon:0

I didn't configure the network system, everything is out of the box.

Can someone help me having just one interface ?

thank you :)

---

