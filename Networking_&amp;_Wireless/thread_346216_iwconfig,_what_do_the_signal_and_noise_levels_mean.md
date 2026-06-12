---
title: "iwconfig, what do the signal and noise levels mean?"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2007-01-25
What do my iwconfig's signal and noise levels mean?

Downloading any files has become slower and slower despite having a 8Meg ADSL service. Using some of the web based speed test sites recent download speeds have been 39Kbps, 128Kbps - and that's after several attempts. I've raised the issue with my ISP and I will be reporting back to them.

Unfortunately today even accessing my  Netgear router's browser page seems slow.

Anyway, I'd like some confirmation that the signal and noise level in my iwconfig isn't abnormal. Noise level :-221 dBm is that good or bad? Tx-power: 0 dBm  good or bad? I've just been able to open another web page as I type without a problem.

ra0       RT2500 Wireless  ESSID:"WiFi"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: "my access point's MAC"   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr : off   Fragment thr : off
          Link Quality=67/100  Signal level=-79 dBm  Noise level:-221 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by evilghost on 2007-01-25
You have a good deal of noise on that frequency and your signal strength is very low.  Try another channel other than 11.  I have good luck with CH 3 (2.422 GHz)

---

