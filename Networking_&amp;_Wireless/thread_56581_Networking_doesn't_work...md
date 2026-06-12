---
title: "Networking doesn't work.."
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by IronKnuckles on 2005-08-13
I just got my Ubuntu install working, but now I have no networking.  :-? 

ifconfig returns **nothing** .

iwconfig returns...
> lo no wireless extensions.<br/>
eth0 no wireless extensions.<br/>
eth1 IEEE 802.11b ESSID:"WLAN" Mode: Managed Frequency: 2.462 GHz Access Point: 00:13:10:7D:F3:98<br/>
Bit rate=11 Mb/s Tx-Power=20 dBm RTS thr: off Frament trot: off<br/>
Power management: off Link quality=100/100 Signal level=-25 dBm Noise level=084 dBm<br/>
Rx invalid nwid:0 Rx invalid crypt: 0 Rxinvalid frag: 0<br/>
Tx excessive retries: 0 Invalid misc:15 Missed beacon: 0 

I have a IPW2200 wireless card built in to my notebook. What really bothers me is that the ethernet doesn't work, so I can't even download the IPW2200 drivers.
Any help?

---

### Post by tehsyco on 2005-08-13
have you tried to up them in ifconfig? 'man ifconfig' ;o - i'm certainly not one to give help though, i'm having massive issues with ipw2200 as well.

---

### Post by andlinux on 2005-08-14
[QUOTE=tehsyco]have you tried to up them in ifconfig? 'man ifconfig' ;o - i'm certainly not one to give help though, i'm having massive issues with ipw2200 as well.[/QUOTE]
I have also an ipw2200 adaptor in my notebook and it worked without doing something. 
Go to "system" > "administration" > "networking"  and configure you wireless card there.

---

