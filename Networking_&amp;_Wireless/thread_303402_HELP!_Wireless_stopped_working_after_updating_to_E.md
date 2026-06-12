---
title: "HELP! Wireless stopped working after updating to Edgy"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by filiphw on 2006-11-20
Help me...

wireless was working fine with 6.06 and Network manager but after updating
to Edgy I can still see my wireless Network name in network manager.. I see my neighbors wireless etc. But if I try to connect it will try for a while (the icon is only spinning around, the two green leds is off) and then timeout. Wired network is working fine. 
.
What can be wrong? The /etc/network/interfaces only cover the lo interface.
.
I try to completly uninstall/install. The only difference is now its asking for the password everytime but still no connection or IP. 


iwconfig during connection attempt:

root@ubuntu-pc:/etc# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"Filiph-NET"  Nickname:"Filiph-NET"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:54  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


========
iwconfig after it has timeout:

root@ubuntu-pc:/etc/wpa_supplicant# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""  Nickname:"Filiph-NET"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:36  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
 

// pls help

---

