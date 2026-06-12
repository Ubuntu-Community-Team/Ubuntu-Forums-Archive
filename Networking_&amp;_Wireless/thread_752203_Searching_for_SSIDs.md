---
title: "Searching for SSIDs"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by willtell on 2008-04-11
I recently purchased a System 76 Pangolin value with Gutsy.  It has the Intel pro 4965 AGN wireless card.  The first time I started the computer, I was able to see available wireless networks, but it disappeared when I tried to change networks and it hasn't come back again.  

 I can connect to wireless networks but only using manual configuration.  If I select "enable roaming" nothing happens, at least nothing I can see.  What do I need to do to search for wireless networks?  
 
 I reinstalled network manager gnome, but that didn't do anything.  I've tried wicd, but that didn't work either.  Thanks for your help.  

Will

---

### Post by dstew on 2008-04-11
Post the output of```
iwconfig
```

---

### Post by willtell on 2008-04-11
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:A2: DB: 0E:90   
          Bit Rate=54 Mb/s   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality=85/100  Signal level=-48 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by nick.ncs on 2008-04-11
try using wi-fi Radar
[http://wifi-radar.systemimager.org/]("http://wifi-radar.systemimager.org/")

---

