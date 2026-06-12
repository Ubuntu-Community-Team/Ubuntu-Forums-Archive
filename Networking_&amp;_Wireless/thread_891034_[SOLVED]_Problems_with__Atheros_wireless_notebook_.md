---
title: "[SOLVED] Problems with  Atheros wireless notebook adapter"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by clausjuhl on 2008-08-15
Hi

I have a laptop with a wireless (built in) network controller (intel). However I bought a Linksys WPC300N Notebook adapter.

If I run "lspci -v | grep Atheros" I get 

16:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)

Thus I know that Ubuntu (8.04) did find the card. However if I do

ifconfig or iwconfig no ath0 is available.

I tried following some threads about installing "madwifi" but still no luck. By the way: The reason why I which to use my Linksys adapter instead of the buildin "Intel" is that I need to be able to change to "monitor mode"

I hope that you have some helpful thoughts.....

---

### Post by clausjuhl on 2008-08-15
I am running ubuntu 8.04 on a lenovo T60.

just to provide some basic results: iwconfig returns

lo        no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"....."  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1D:7E:AB:B2:9A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:"........" *(changed when copying the text)*
          Power Management:off
          Link Quality=84/100  Signal level=-50 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

