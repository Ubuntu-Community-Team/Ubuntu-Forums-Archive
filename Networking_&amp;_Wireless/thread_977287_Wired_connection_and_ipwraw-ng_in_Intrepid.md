---
title: "Wired connection and ipwraw-ng in Intrepid?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by RRFarFar on 2008-11-10
Hi everybody,
Does anyone have a clue how to get ipwraw-ng working in Ibex? I guess there is some kind of problem with kernel 2.26.27 that is why it is not working or maybe I have missed something.
I have used to webpages to install ipwraw-ng on my 8.10:
1. [http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945) - Injection Walkthrough
2. [http://ubuntuforums.org/showthread.php?t=688367](http://ubuntuforums.org/showthread.php?t=688367) - Trying to install ipwraw-ng
Both pages are good, but not good enough to get ipwraw-ng working in Ubuntu Intrepid.
If I do IWCONFIG it gives me the following interfaces:
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"XXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=43/100  Signal level:-83 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions. - WHAT KIND OF CONNECTION IS THIS?????

If I do IFCONFIG it gives me the following interfaces:
A. lo        
B. wlan0    
C. wmaster0  

Could anyone help to install ipwraw-ng on IBEX? My personal awkward installation did not do the trick and at the moment my WIRED connection is not working at all.I would like to restore wired connection at least
Thanks for your time in advance

---

### Post by RRFarFar on 2008-11-10
I really need help on this one. Maybe some Gurus can help

---

### Post by RRFarFar on 2008-11-11
Ok, just forget. I guess there is no need to install ipwraw in intrepid for 3945ABG. One should search the whole web to find it out. A lot fo people do know about this, but they just simply non-reponsive, or whatever it is called in English. I have to reinstall intrepid again and make it secondary system, because I did spend a lot fo time tweaking things which very working from the start in XP.
I saw a thread in this forum with some stupid title, like WHAT ARE YOU LISTENING RIGHT NOW??? I even replied to it, than I thought it would great to ban such people who really take others' attention for nothing.
As it many times happened people just do not answer.

---

