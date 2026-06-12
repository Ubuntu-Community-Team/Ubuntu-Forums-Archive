---
title: "Detects wireless networks, will not connect to them"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Roisen.dubh on 2007-04-30
My wireless card detects my wireless network, but will not connect to it.

In the network status drop-down menu, next to the date in the taskbar, I can see my wireless network, but it shows a signal strength of 0%.

When I run iwconfig I get this:

```
ra1       RT61 Wireless  ESSID:"Doppelganger"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:05:11:10:F3   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-49 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

As you can see, my signal strength here differs from the one given in the taskbar, also my access point is associated.

When I try to choose my network, a circle spins around two dots, which I assume means that it is connecting. However, after a few moments time, It will default back to the wired network. I've tried using ndiswrapper, however that did not work.

Any ideas?

---

### Post by rpasell on 2007-05-26
I am also having this problem.  All networks show up in wifi radar, with 0 signal strength.  Here is my iwconfig output.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It was working fine in Feisty 2 days ago, the I downloaded an update (2 packages).  I left the laptop unplugged and the battery died, when I booted up wireless wasn't working.

---

