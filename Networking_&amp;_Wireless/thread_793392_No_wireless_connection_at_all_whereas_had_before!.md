---
title: "No wireless connection at all whereas had before!"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by srdempster on 2008-05-13
I have lost all wireless connection on my dell vostro 1000. First used ndiswrapper successfully to use my dell wlan1390 card, then that went pear-shaped.So used my Belkin usb wlan dongle with success and 54mbs.No I've lost wireless completely if I hover over gnome's applet in my panel it just shows wired connection only and if right-clicked enable wired it's ticked but wireless is unticked and greyed out?Here's my iwconfig output:

steve@steve-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

Any ideas?? Apologies for last post which I've cancelled but it does make me scream!Linux is ace but it sure does break and I've not got the skills yet to know everything.What good books do I buy or good LUG groups/website I can join???

Steve

---

