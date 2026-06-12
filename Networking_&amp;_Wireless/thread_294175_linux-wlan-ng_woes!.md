---
title: "linux-wlan-ng woes!"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by animammal on 2006-11-06
Hi
I'm having a few probs getting network connectivity on my d- link dwl-122 in edgy and i'm hoping someone could help out. The USB dongle it's self seems to be working just fine with Linux-wlan-ng as you can see from the iwconfig printout below. I've been using edgy for about a month and it's the first Linux OS I've used. 

wlan0     
IEEE 802.11-b  ESSID:"swatchways" Nickname:"swatchways"
Mode:Managed  Frequency:2.462 GHz Access Point:11:50:83:BB:37      Bit Rate:11 Mb/s   Tx-Power:18 dBm   
Retry min limit:8   RTS thr.off   Fragment thr.off
Encryption key.off
Link Quality=26/92  Signal level=-64 dBm  Noise level=-90 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Signal strength is good and there is no security to worry about. 

The little network icon on the desktop panel shows it is connected. my router registers this computer as a dhcp client but i cannot ping anything apart from 127.0.0.1:confused: 

I've looked around the internet for ages but i can't find anything that helps! :-| 

If you've got any suggestions then id really like to hear them!!

Thanks in advance.

---

### Post by Yourname on 2006-11-06
You're lucky you even got it to work.
It's not working for me, with ndiswrapper, and with linux-wlan-ng.

---

