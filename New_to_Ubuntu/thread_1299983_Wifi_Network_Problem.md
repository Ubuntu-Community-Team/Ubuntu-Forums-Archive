---
title: "Wifi Network Problem"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by jhonnytunes on 2009-10-24
Hi everyone. Ive recently installed Ubuntu 9.04 on my Laptop(Toshiba Satellite A55-s106).I was a little nervous cause I tought Linux would have incopatibility problem. I cannot search for avaliable wrireless networks like i use to do in wondows. It doenst matter if I have to scan in the terminal. Im having this outputs. If you need more to now my issue tell me this way. Thank you. 



"iwconfig"
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

--------------------

"iwlist ath0 scanning ath0"  
 No scan results

---

### Post by bkratz on 2009-10-24
> **jhonnytunes said:**
> Hi everyone. Ive recently installed Ubuntu 9.04 on my Laptop(Toshiba Satellite A55-s106).I was a little nervous cause I tought Linux would have incopatibility problem. I cannot search for avaliable wrireless networks like i use to do in wondows. It doenst matter if I have to scan in the terminal. Im having this outputs. If you need more to now my issue tell me this way. Thank you. 



"iwconfig"
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

--------------------

"iwlist ath0 scanning ath0"  
 No scan results


Generally with network manager you can simply left click on the icon (the vertical bars at the top right) and see the available AP's.

---

### Post by jhonnytunes on 2009-10-24
> **bkratz said:**
> Generally with network manager you can simply left click on the icon (the vertical bars at the top right) and see the available AP's.

Sorry but this time this isnt woriking.

LEFT CLICK OUTPUT:

Wired Networks
(  )Auto eth0
Wireless NEtworks
VPN Connections >
Connect to hidden wireless network...
Create new wireless network.



RIGHT CLICK OUTPUT

[  ]Enable Networking
[  ]Enable Wireless
Connection Information
Edit Connections
About

-----
[  ] means Check box.
(  )means Radiobutton

All is checked and selected.

---

