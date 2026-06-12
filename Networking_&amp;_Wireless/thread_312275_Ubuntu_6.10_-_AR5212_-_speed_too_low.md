---
title: "Ubuntu 6.10 - AR5212 - speed too low"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Striatum on 2006-12-04
Hi all!

I have Ubuntu Edgy Eft running with a PC-Card Atheros AR5212 card and
WPA-TKIP. Everything works fine so far, but the speed I have is
(compared to windows) somehow too slow.
The AP is about 10 m away from my laptop and I constantly get a 54M
connection with about 2 Mbyte/s transfer rate with Windows XP.
In linux I mostly get "Bit Rate:5 Mb/s" with "iwconfig ath0" and "Link
Quality=20/94".
I have enabled
iwpriv ath0 mode 0
iwpriv ath0 turbo 1
modprobe ath_pci countrycode=276


Full output of iwconfig ath0:

--------------------
ath0      IEEE 802.11g  ESSID:"Corpus" 
          Mode:Managed  Frequency:2.472 GHz  Access Point:
00:04:0E:2B:4C:ED  
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:439  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------------------

I already tried ndiswrapper, which gives me the same speed as with windows - but it is unable to display link quality / signal strength, it's always 100%.

anyone got an idea?

thank you very much!
Dominik

---

