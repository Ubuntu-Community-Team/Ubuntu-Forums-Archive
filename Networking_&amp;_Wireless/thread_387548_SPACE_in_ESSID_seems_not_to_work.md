---
title: "SPACE in ESSID seems not to work"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by info2 on 2007-03-18
Heya.

I want to connect to my company's wireless network. With Windows (I'm sorry) there isn't a problem but with Linux.

The ESSID looks like "my company" <- notice the space

Networkmanager find this network and i also can use iwconfig to set the essid if I put it in quotes ( "my company" ). 
But the card still cannot associate with the AP. I noticed the raising "Rx invalid nwid" value.

ath0   IEEE 802.11g  ESSID:"my company"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:12:BF:5A:C0:F5   
          Bit Rate: 0 kb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:8249  Rx invalid crypt:0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

"man iwconfig" tells me that if this value raises there is a misstyped essid or bssid. 
So i think Linux is not able to handle the space in the essid.

Is there anything i can do? May the reason be a different charset?

Its an Atheros Chipset wirg madwifi-ng - drivers, I am using Edgy and Feisty.

Thanks for any help

---

### Post by encompass on 2007-03-18
Spaces are always bad with things like this.  Try taking that out.  OR for the heck of it... try 'my space' instead of the double quotes.

---

### Post by info2 on 2007-03-18
Already tried single quotes.
Yes, spaces are bad things ... damn WoW (Word of Windows)

---

