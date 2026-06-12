---
title: "Problem changing the bit rate"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Sioux_Soldat on 2009-02-25
I am having problems increasing the speed of my network connection. My iwconfig is:

[COLOR="Red"]wlan1     IEEE 802.11bgn  ESSID:"MicMac II"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:9B:C8:BF   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry limit:8   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=34/100  Signal level:-73 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR]

I tried this command to increase the bit rate (which I am assuming will increase the speed of my connection:

 [COLOR="Red"]sudo iwconfig wlan1 rate 54M[/COLOR]

no effect. My speed remains at 1 mb/s

I am running Ubuntu 8.1 on an ASUS N10J with a wireless N connection. Any help would be appreciated.

---

### Post by unutbu on 2009-02-26
What happens if you sit the router right next to the wireless card? Shut down the machine, then power on to force the wireless card to establish a new connection. Run iwconfig. Is the bit rate any higher?

---

### Post by Sioux_Soldat on 2009-02-26
No difference when I'm right next to the router. This is a dual boot machine and when I'm running under windows the speed is blazing.

---

